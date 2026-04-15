# Model Serving Best Practices

> Patterns extracted from vLLM, Ollama, and HF Transformers for production LLM serving.

*Sources: vllm-project/vllm (77k⭐), ollama/ollama (169k⭐), huggingface/transformers (159k⭐)*

## 1. OpenAI-Compatible API Pattern

**Why**: Every LLM client library expects OpenAI's API format. Providing compatibility = zero migration cost.

**Pattern** (from vLLM + Ollama):
```
POST /v1/chat/completions
{
  "model": "llama3",
  "messages": [{"role": "user", "content": "Hello"}],
  "stream": true,
  "temperature": 0.7
}
```

**Key decisions**:
- Stream responses by default (SSE format)
- Support both `/v1/completions` and `/v1/chat/completions`
- Return usage stats (prompt_tokens, completion_tokens)
- Support function calling / tool use format

## 2. Memory Management (PagedAttention)

**Why**: KV cache is the #1 memory bottleneck for LLM serving.

**Pattern** (from vLLM):
- Treat KV cache like OS virtual memory pages
- Allocate blocks on-demand, not pre-allocated
- Share KV cache blocks across requests with same prefix
- Result: 2-4x higher throughput vs naive allocation

**Lesson for SaaS**: If building an LLM-powered product, use vLLM or Ollama for serving. Don't reinvent memory management.

## 3. Quantization for Cost Reduction

**Why**: FP16 → INT4 = 4x memory reduction = 4x more users per GPU.

**Tiers** (from HF Transformers + vLLM):
| Method | Size Reduction | Quality Loss | Use Case |
|--------|---------------|-------------|----------|
| FP8 | 2x | <1% | Production serving |
| INT8 (GPTQ) | 2x | 1-2% | Cost-sensitive production |
| INT4 (AWQ/GPTQ) | 4x | 2-5% | Local dev, edge |
| GGUF (Ollama) | 2-8x | Varies | Local, consumer hardware |

## 4. Continuous Batching

**Why**: Static batching wastes GPU cycles waiting for longest sequence.

**Pattern** (from vLLM):
- Process tokens as they arrive, not in fixed batches
- Insert new requests into running batch immediately
- Remove completed sequences without waiting for batch
- Result: 10-20x throughput improvement for variable-length workloads

## 5. Speculative Decoding

**Why**: Use a small/fast model to draft tokens, verify with large model in parallel.

**Pattern** (from vLLM v0.19.0):
- Draft model generates N candidate tokens
- Target model verifies all N tokens in one forward pass
- Accept correct tokens, reject and regenerate from first mismatch
- Result: 2-3x speedup with no quality loss

## Deployment Architecture

```
[Client App (TypeScript/Next.js)]
         |
    [API Gateway]
         |
   [Load Balancer]
    /          \
[vLLM Server 1]  [vLLM Server 2]   ← Production (GPU)
    or
[Ollama]                             ← Development (local)
```

**Key Principle**: Use Ollama for development, vLLM for production. Same API format.
