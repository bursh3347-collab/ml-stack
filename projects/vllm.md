# vLLM

> High-throughput, memory-efficient LLM inference and serving engine.

| Metric | Data |
|--------|------|
| GitHub | https://github.com/vllm-project/vllm |
| Stars | 76,687 |
| Forks | 15,620 |
| License | Apache-2.0 |
| Language | Python / C++ / CUDA |
| Latest Release | v0.19.0 (2026-04-03, 12 days ago) |
| Open Issues | 4,277 |
| Last Commit | 2026-04-15 (today) |

## TEMC Scoring

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 90 | PagedAttention (2-4x throughput), continuous batching, speculative decoding, FP8/NVFP4 quantization, FlashInfer MLA, OpenAI-compatible API. Blackwell B300 support. 448 commits in v0.19.0 alone. |
| E (Ecosystem) | 88 | 76k stars, 15k forks, 197 contributors per release. UC Berkeley origin → Linux Foundation. Used by: Anyscale, AWS, Azure, etc. Rapid growth (+26k stars in months). |
| M (Market) | 92 | LLM serving is THE infrastructure bottleneck. Every company deploying LLMs needs efficient inference. vLLM is becoming the default. Perfect timing. |
| C (Combo) | 78 | Python/C++/CUDA (not TypeScript). Server-side only. But critical for any LLM product deployment. OpenAI-compatible API = integrate from天子's TypeScript apps. Learning cost: medium. |
| **Composite** | **87** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Analysis

```
vllm/
├── vllm/
│   ├── engine/           # Core engine (V1 + V2 runner)
│   ├── model_executor/   # Model execution layer
│   ├── worker/           # Distributed worker
│   ├── attention/        # Attention backends (FlashAttention, FlashInfer)
│   ├── spec_decode/      # Speculative decoding
│   ├── quantization/     # Quantization (FP8, GPTQ, AWQ, NVFP4)
│   ├── entrypoints/      # API servers (OpenAI, embeddings)
│   └── distributed/      # TP/PP/EP support
├── csrc/                 # C++/CUDA kernels
├── benchmarks/           # Performance benchmarks
└── tests/               # Test suite
```

**Architecture Pattern**: Engine-Worker pattern, PagedAttention memory management, plugin-based attention backends.

**Key Innovation**: PagedAttention — manages KV cache like OS virtual memory pages, enabling 2-4x higher throughput.

## Core Modules

1. **PagedAttention Engine** — KV cache paging system (large, high coupling)
2. **Model Executor** — Model loading and execution (large, medium coupling)
3. **OpenAI-Compatible Server** — REST API endpoint (medium, low coupling)
4. **Quantization** — FP8/NVFP4/GPTQ/AWQ support (medium, low coupling)
5. **Speculative Decoding** — Draft-verify acceleration (medium, medium coupling)

## Extractable Components

| Module | Difficulty | Est. Time | Target |
|--------|-----------|-----------|--------|
| OpenAI server pattern | Simple copy | 2h | code-base/ai-integration/ |
| Model serving architecture | Documentation | 4h | best-practices/model-serving.md |
| Quantization recipes | Documentation | 2h | best-practices/ |
| Benchmarking framework | Need adaptation | 4h | code-base/ |

⭐ **Universal Code Candidate**: OpenAI-compatible API server, model serving deployment patterns.

## Business Value

- **Pain Point**: LLM inference cost and latency (致命级)
- **TAM**: LLM inference market $50B+ by 2028
- **Monetization**: vLLM is free. Value for天子: reduce inference costs for AI SaaS products.
- **Differentiation**: Optimize serving costs = competitive advantage in Micro SaaS.

## Why It Might NOT Be Worth Deep Investment

- 🔴 Heavy CUDA dependency — requires GPU infrastructure
- 🔴 Complex codebase — C++/CUDA kernels not accessible to most
- 🟡 Rapidly evolving API — frequent breaking changes
- ✅ But THE standard for LLM serving — must know architecture
- ✅ OpenAI-compatible = easy integration
