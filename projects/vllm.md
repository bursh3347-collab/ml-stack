# vLLM

> A high-throughput and memory-efficient inference and serving engine for LLMs

| Metric | Data |
|------|------|
| GitHub | https://github.com/vllm-project/vllm |
| Stars | 76,691 |
| Forks | 15,621 |
| License | Apache-2.0 |
| Language | Python / C++ / CUDA |
| Last Updated | 2026-04-15 |
| Open Issues | 4,279 |
| Created | 2023-02-09 |

## TEMC Scoring

| Dimension | Score | Rationale |
|------|------|------|
| T (Tech) | 92 | PagedAttention breakthrough — 2-4x throughput over naive serving. Continuous batching, tensor parallelism, speculative decoding. CUDA/ROCm/XPU/TPU/CPU multi-platform. FlashAttention integration. |
| E (Ecosystem) | 88 | 76k stars, 15k forks. Rapid growth. Industry adoption: used by major AI companies for production serving. OpenAI-compatible API. Active development (multiple commits daily). |
| M (Market) | 90 | LLM serving is critical infrastructure. Every company deploying LLMs needs efficient inference. Market growing with LLM adoption. vLLM is the de facto standard for self-hosted LLM serving. |
| C (Combo) | 72 | Python/CUDA — infrastructure-heavy, requires GPU expertise. Not directly SaaS-applicable for 天子. But understanding serving patterns is valuable for building AI products. OpenAI-compatible API is reusable. |
| **Composite** | **86** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value
vLLM's PagedAttention algorithm revolutionized LLM serving by treating KV cache memory like virtual memory pages. This simple insight enables 2-4x higher throughput than naive implementations. It's now the standard engine behind most self-hosted LLM deployments.

## Architecture Highlights
- **PagedAttention**: Virtual memory-inspired KV cache management, near-zero waste
- **Continuous Batching**: Dynamic request batching for maximum GPU utilization
- **Tensor Parallelism**: Multi-GPU serving with automatic sharding
- **Speculative Decoding**: Draft model + verification for faster generation
- **OpenAI-Compatible API**: Drop-in replacement for OpenAI API endpoints
- **Multi-Backend**: CUDA, ROCm, XPU, TPU, CPU support
- **Quantization**: GPTQ, AWQ, FP8, MXFP4 for reduced memory footprint

## Key Modules
1. **PagedAttention Engine** — Core KV cache management (large, core)
2. **Scheduler** — Request scheduling and continuous batching (medium, core)
3. **Model Loader** — HuggingFace model loading and conversion (medium, independent)
4. **API Server** — FastAPI-based OpenAI-compatible endpoints (medium, independent)
5. **Distributed Engine** — Tensor/pipeline parallelism (large, complex coupling)

## Extractable Patterns
- ⭐ **通用代码候选**: OpenAI-compatible API server pattern (FastAPI) → code-base/ai-integration/api-server/
- ⭐ **通用代码候选**: Continuous batching / request queue pattern → code-base/ai-integration/serving/
- Model quantization integration patterns

## Business Value
- **Pain Point**: Cost-effective LLM serving at scale (Critical for AI companies)
- **Target Users**: AI companies, enterprises self-hosting LLMs
- **Monetization**: LLM serving infrastructure, managed inference service
- **差异化窗口**: Combined with Ollama (dev) + vLLM (prod) = complete local→production pipeline

## Why It Might NOT Be Worth It (反证)
- Requires GPU infrastructure expertise and significant hardware investment
- For a one-person company, cloud API (OpenAI/Claude) is more cost-effective at low volumes
- CUDA-heavy codebase is very specialized — steep learning curve
- Ollama covers the local inference use case more simply

## 天子 Verdict
🟡 **MEDIUM PRIORITY** — Essential knowledge for understanding LLM infrastructure, but not immediately actionable for 天子's SaaS strategy. Learn the concepts (PagedAttention, continuous batching) rather than the code. When 天子's product needs self-hosted inference, vLLM is the answer.
