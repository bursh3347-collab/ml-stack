# Ollama

> Docker for LLMs — run any open-source model locally with one command.

| Metric | Data |
|--------|------|
| GitHub | https://github.com/ollama/ollama |
| Stars | 169,070 |
| Forks | 15,596 |
| License | MIT |
| Language | Go |
| Last Commit | 2026-04-15 (today) |
| Open Issues | 2,944 |

## TEMC Scoring

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 85 | Clean Go implementation, Docker-like UX (`ollama run llama3`), OpenAI-compatible API, quantization (GGUF), multi-model support. Supports Kimi-K2.5, GLM-5, MiniMax, DeepSeek, Qwen, Gemma. |
| E (Ecosystem) | 92 | 169k stars (top 5 in all of GitHub), 15k forks. Explosive growth. Community: extensions, GUIs (Open WebUI 75k⭐), IDE integrations. |
| M (Market) | 90 | Local LLM is the hottest trend — privacy, cost reduction, offline capability. Perfect timing with open-weight models (Llama, Qwen, DeepSeek). |
| C (Combo) | 85 | MIT license. OpenAI-compatible API = drop-in replacement in天子's apps. Directly usable for local dev/testing. Ideal for Micro SaaS that needs local AI. |
| **Composite** | **88** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Analysis

```
ollama/
├── cmd/              # CLI entry points
├── server/           # HTTP API server (OpenAI compatible)
├── llm/              # LLM runtime (llama.cpp bindings)
├── gpu/              # GPU detection and management
├── format/           # Model format handling (GGUF)
├── runners/          # Model execution runners
└── api/              # Go client library
```

**Architecture Pattern**: Single binary, client-server, REST API, GGUF model format.

## Core Modules

1. **Server/API** — OpenAI-compatible HTTP server (medium, low coupling)
2. **LLM Runtime** — llama.cpp-based inference (large, high coupling with GPU)
3. **Model Management** — Pull/create/list/delete models (medium, low coupling)
4. **GPU Detection** — Multi-GPU and VRAM management (small, medium coupling)
5. **Format/GGUF** — Model format parsing and quantization (medium, medium coupling)

## Extractable Components

| Module | Difficulty | Est. Time | Target |
|--------|-----------|-----------|--------|
| OpenAI-compatible API pattern | Simple copy | 2h | code-base/ai-integration/ |
| Model management CLI pattern | Need adaptation | 4h | code-base/ |
| GPU detection logic | Documentation | 2h | best-practices/ |

⭐ **Universal Code Candidate**: OpenAI-compatible API server pattern (reusable for any LLM wrapper).

## Business Value

- **Pain Point**: Running LLMs locally without cloud costs (重要级)
- **TAM**: Local AI market growing rapidly, tied to privacy regulations
- **Monetization**: Ollama itself is free. For天子: use as local backend for SaaS products.
- **Differentiation**: Build Micro SaaS tools that leverage Ollama as local inference engine.

## Why It Might NOT Be Worth Deep Investment

- 🟡 Go language (not TypeScript), but API is language-agnostic
- 🟡 Dependent on llama.cpp upstream (single point of failure)
- 🟡 Enterprise features limited (no auth, no rate limiting built-in)
- ✅ MIT license = maximum commercial flexibility
- ✅ OpenAI-compatible API = zero migration cost
