# PyTorch

> The dominant deep learning framework — dynamic computation graphs, GPU acceleration, and production-grade tooling.

| Metric | Data |
|--------|------|
| GitHub | https://github.com/pytorch/pytorch |
| Stars | 99,144 |
| Forks | 27,495 |
| License | BSD-3-Clause |
| Language | Python / C++ |
| Latest Release | v2.11.0 (2026-03-23) |
| Open Issues | 18,534 |
| Last Commit | 2026-04-15 (today) |

## TEMC Scoring

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 92 | Production-grade code, FlexAttention w/ FlashAttention-4 on Blackwell, CUDA 13.0 default, torch.compile matured, XPU Graph support, MPS Apple Silicon expansion. Architecture: dynamic graph + eager mode + compiler optimization. Doc quality: excellent (pytorch.org). |
| E (Ecosystem) | 95 | 99k stars, 27k forks, 3000+ contributors, Meta-backed. PyTorch Foundation under Linux Foundation. Dominant in research (>80% papers). Ecosystem: torchvision, torchaudio, torchtext, lightning, HuggingFace all built on it. |
| M (Market) | 75 | Framework itself not monetizable, but foundational infrastructure. Market position: #1 in research, gaining in production (overtook TF). Late-stage maturity — value is as dependency, not standalone product. |
| C (Combo) | 70 | Python (not TypeScript), but foundation for all AI work. vLLM, HF Transformers, LlamaIndex all depend on it. Heavy (can't embed in Micro SaaS directly), but essential for model training/fine-tuning. Learning cost: medium-high. |
| **Composite** | **82** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Analysis

```
pytorch/
├── torch/           # Python frontend (nn, autograd, optim, compile)
├── aten/            # C++ tensor library (ATen)
├── c10/             # Core library (allocators, dispatch, streams)
├── caffe2/          # Legacy (being phased out)
├── torchgen/        # Code generation for ops
├── functorch/       # Function transforms (vmap, grad)
└── test/            # Comprehensive test suite
```

**Architecture Pattern**: Monorepo, multi-language (Python/C++/CUDA), dispatcher-based op resolution.

**Key Dependencies**: CUDA, cuDNN 9.19, NCCL, MKL/oneDNN, Triton.

**Baseline Stack Match**: 6/10 — Python (not TypeScript), but universal AI foundation.

## Core Modules

1. **torch.nn** — Neural network layers and loss functions (large, low coupling)
2. **torch.compile / Dynamo / Inductor** — Compiler stack for optimization (large, medium coupling)
3. **torch.distributed** — Distributed training (FSDP, DTensor, TP/PP) (large, medium coupling)
4. **torch.autograd** — Automatic differentiation engine (medium, high coupling with aten)
5. **FlexAttention** — Flexible attention with Flash backend (medium, low coupling)

## Extractable Components

| Module | Difficulty | Est. Time | Target |
|--------|-----------|-----------|--------|
| FlexAttention patterns | Need adaptation | 4-8h | code-base/ai-integration/ |
| torch.compile best practices | Documentation | 2-4h | best-practices/ |
| Distributed training patterns | Documentation | 4-8h | best-practices/ |
| Model serving pipeline | Need adaptation | 8-16h | code-base/deploy/ |

⭐ **Universal Code Candidate**: torch.compile optimization patterns, distributed training recipes.

## Business Value

- **Pain Point**: Model training/inference infrastructure (致命级)
- **TAM**: $47B+ AI/ML market
- **Monetization**: Not directly — it's infrastructure. Value is as enabler for天子's AI products.
- **Differentiation Window**: None (mature). Value is in mastery, not modification.

## Why It Might NOT Be Worth Deep Investment

- 🔴 Too large and complex for one-person operation to contribute meaningfully
- 🔴 Python-only, doesn't match TypeScript baseline stack
- 🔴 Mature framework — no differentiation opportunity
- 🟡 Learning curve is steep for advanced features (compile, distributed)
- ✅ But essential knowledge for any AI product builder
