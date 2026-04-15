# vLLM

> Easy, fast, and cheap LLM serving for everyone.

| Metric | Data |
|--------|------|
| GitHub | [vllm-project/vllm](https://github.com/vllm-project/vllm) |
| Stars | ~50,000 |
| Forks | ~8,000 |
| License | Apache-2.0 |
| Language | Python + C++/CUDA |
| Last Update | 2026-04 (very active) |
| Contributors | 700+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 92 | PagedAttention (24x throughput). Continuous batching. Speculative decoding. Tensor parallelism. SOTA inference. |
| E Ecosystem | 85 | 50k stars, UC Berkeley origin. Adopted by major AI companies. Active development pace. |
| M Market | 88 | LLM serving is critical infrastructure. Every company deploying LLMs needs efficient inference. Cost reduction is key. |
| C Combo | 68 | Python/CUDA (not TypeScript). But provides OpenAI-compatible API = consume from any language. Infrastructure knowledge essential. |
| **Overall** | **84** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 83.8 |

## Core Value
The fastest open-source LLM inference engine. PagedAttention manages GPU memory like OS virtual memory, achieving 24x higher throughput than naive serving. Critical infrastructure for production LLM deployment.

## Architecture Highlights
- **PagedAttention**: KV cache managed in non-contiguous blocks (like OS virtual memory)
- **Continuous Batching**: Dynamic batch formation for maximum GPU utilization
- **Speculative Decoding**: Small model drafts, large model verifies for faster generation
- **Tensor Parallelism**: Split model across multiple GPUs
- **OpenAI-Compatible API**: Drop-in replacement for OpenAI API
- **Quantization**: AWQ, GPTQ, FP8 support for model compression

## Extractable Patterns
- PagedAttention memory management concept
- Continuous batching for throughput optimization
- OpenAI-compatible serving API
- Model parallelism strategies
