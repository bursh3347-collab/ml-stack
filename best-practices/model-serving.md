# Best Practices: Model Serving

> Extracted from PyTorch, vLLM, Ollama, HuggingFace Transformers

## Overview

Model serving is the process of making trained ML/LLM models available for inference via APIs. This document captures best practices from the top open-source serving solutions.

## Pattern 1: OpenAI-Compatible API (from Ollama + vLLM)

**Source**: Ollama (169k⭐, MIT) + vLLM (76k⭐, Apache-2.0)

**Why This Pattern**: The OpenAI API has become the de facto standard. Building OpenAI-compatible endpoints means any client library works out of the box.

```python
# Core pattern: FastAPI + OpenAI-compatible endpoint
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class ChatRequest(BaseModel):
    model: str
    messages: list[dict]
    temperature: float = 0.7
    max_tokens: int = 1024
    stream: bool = False

@app.post("/v1/chat/completions")
async def chat_completions(request: ChatRequest):
    # Route to appropriate backend (Ollama, vLLM, OpenAI)
    response = await inference_engine.generate(
        messages=request.messages,
        temperature=request.temperature,
        max_tokens=request.max_tokens
    )
    return {
        "id": f"chatcmpl-{uuid4()}",
        "object": "chat.completion",
        "model": request.model,
        "choices": [{"message": {"role": "assistant", "content": response}}]
    }
```

**Key Takeaway**: Always build OpenAI-compatible APIs. This gives you backend flexibility — swap between Ollama (dev), vLLM (self-hosted), and OpenAI (cloud) without changing client code.

## Pattern 2: Continuous Batching (from vLLM)

**Source**: vLLM (76k⭐, Apache-2.0)

**Why This Pattern**: Naive batching wastes GPU memory on padding. Continuous batching adds/removes requests dynamically.

**Core Concept**:
- Traditional: Wait for batch to fill → process all → return all
- Continuous: Process requests as they arrive, interleave at token level
- Result: 2-4x higher throughput

**When to Use**: Self-hosted LLM serving with >10 concurrent users.

## Pattern 3: Model Versioning (from TF Serving + HuggingFace)

**Source**: TF Serving + HuggingFace Hub

**Best Practice**: Treat models like code — version, tag, A/B test.

```
models/
├── v1/
│   ├── model.safetensors
│   └── config.json
├── v2/
│   ├── model.safetensors
│   └── config.json
└── serving_config.yaml  # Routes: 90% v2, 10% v1
```

## Pattern 4: Graceful Degradation

**Best Practice from all projects**: Build a fallback chain for reliability.

```
Primary:   vLLM self-hosted (lowest cost, highest control)
  ↓ fail
Fallback:  Ollama local (works offline)
  ↓ fail  
Fallback:  OpenAI API (always available, higher cost)
```

## Anti-Patterns

1. **Single-provider lock-in**: Always abstract your LLM provider behind an interface
2. **No streaming**: LLM responses should always support streaming for good UX
3. **Synchronous serving**: Always use async/await for LLM inference calls
4. **No timeout**: LLM inference can hang — always set timeouts
5. **No caching**: Cache identical prompts to reduce cost and latency
