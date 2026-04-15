# Model Serving & Deployment Best Practices

> Patterns extracted from vLLM, Ollama, TF Serving, and production ML systems.

## Pattern 1: OpenAI-Compatible API (from Ollama + vLLM)

The de facto standard for LLM serving:

```typescript
// Client code works with OpenAI, Ollama, vLLM, or any compatible server
const response = await fetch('http://localhost:11434/v1/chat/completions', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    model: 'llama3',
    messages: [{ role: 'user', content: 'Hello!' }],
    stream: true,
  }),
});
```

**Why this matters**: Write once, deploy anywhere. Same client code for local Ollama dev, vLLM production, or OpenAI fallback.

## Pattern 2: Model Registry Pattern (from HuggingFace)

```
Registry → Download → Load → Cache → Serve
```

1. **Registry**: Central model catalog with metadata (size, license, benchmarks)
2. **Download**: Chunked download with resume, checksum verification
3. **Load**: Lazy loading, quantization on load, device mapping
4. **Cache**: Local cache with LRU eviction, shared across applications
5. **Serve**: HTTP API with health checks, metrics, versioning

## Pattern 3: Streaming Response (Essential for LLM UX)

```typescript
async function* streamChat(messages: Message[]): AsyncGenerator<string> {
  const response = await fetch('/v1/chat/completions', {
    method: 'POST',
    body: JSON.stringify({ messages, stream: true }),
  });
  
  const reader = response.body!.getReader();
  const decoder = new TextDecoder();
  
  while (true) {
    const { done, value } = await reader.read();
    if (done) break;
    
    const lines = decoder.decode(value).split('\n');
    for (const line of lines) {
      if (line.startsWith('data: ') && line !== 'data: [DONE]') {
        const chunk = JSON.parse(line.slice(6));
        yield chunk.choices[0]?.delta?.content ?? '';
      }
    }
  }
}
```

## Pattern 4: GPU Memory Management (from vLLM)

- **KV Cache Management**: Pre-allocate GPU memory for attention cache
- **Dynamic Batching**: Group incoming requests to maximize GPU utilization
- **Model Offloading**: Move inactive layers to CPU/disk when GPU is full
- **Quantization**: Reduce model precision (FP16 → INT8 → INT4) for memory savings

## Pattern 5: Multi-Model Serving

```
Router → Model A (fast, cheap)
       → Model B (slow, smart)
       → Model C (specialized)
```

Routing strategies:
- **Complexity-based**: Simple queries → small model, complex → large model
- **Domain-based**: Code → CodeLlama, general → Llama, vision → LLaVA
- **Cost-based**: Free tier → local model, paid tier → cloud API
- **Fallback**: Primary model → fallback model → error response

## Anti-Patterns

1. **No streaming** — Users hate waiting 10+ seconds for a response
2. **No caching** — Same prompt = same response, cache it
3. **Single model** — Use routing for cost/quality optimization
4. **No health checks** — Monitor GPU memory, inference latency, error rates
5. **Synchronous serving** — Always use async for LLM inference
