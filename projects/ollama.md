# Ollama

> Get up and running with large language models locally.

| Metric | Data |
|--------|------|
| GitHub | [ollama/ollama](https://github.com/ollama/ollama) |
| Stars | ~120,000 |
| Forks | ~10,000 |
| License | MIT |
| Language | Go |
| Last Update | 2026-04 (very active) |
| Contributors | 400+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 88 | Simple CLI, model management, OpenAI-compatible API. llama.cpp backend. Multi-model, GPU acceleration. |
| E Ecosystem | 92 | 120k stars, explosive growth. Becoming Docker for LLMs. Massive community model library. |
| M Market | 92 | Local LLM adoption exploding. Privacy-first AI trend. Edge AI growth. Developer-beloved. |
| C Combo | 85 | OpenAI-compatible API = drop-in replacement in TypeScript apps. REST API from any language. MIT license. |
| **Overall** | **90** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 89.7 |

## Core Value
Docker for LLMs. One command to download and run any open-source LLM locally. OpenAI-compatible API means existing apps work with zero code changes. Privacy, speed, no API costs.

## Architecture Highlights
- **Model Management**: `ollama pull` / `ollama run` — Docker-like model lifecycle
- **OpenAI-Compatible API**: `/v1/chat/completions` endpoint, drop-in replacement
- **llama.cpp Backend**: Optimized C++ inference with GGUF quantization
- **Multi-Model**: Run multiple models simultaneously, swap on demand
- **Modelfile**: Dockerfile-like model customization (system prompt, parameters)
- **GPU Acceleration**: CUDA, Metal, ROCm support

## Key Modules
1. **Model Registry** (Large) — Pull, create, push, list, delete models
2. **Inference Server** (Large) — HTTP API with streaming, concurrency
3. **llama.cpp Integration** (Core) — GGUF model loading and inference
4. **Modelfile System** (Small) — Custom model configuration
5. **GPU Manager** (Medium) — Automatic GPU detection and memory management

## Extractable Patterns
- **⭐ Universal Code Candidate: OpenAI-Compatible API Server** → code-base/ai-integration/openai-compat-api/
- Model lifecycle management (pull/run/stop)
- Modelfile configuration pattern
- GPU memory management strategies

## Why #1 Priority for Tianzi
- MIT license, OpenAI-compatible API = zero switching cost
- Local development without API bills
- Privacy-first for sensitive data processing
- Perfect for AI SaaS development and testing
