# PyTorch

> The most popular deep learning framework — from research to production.

| Metric | Data |
|--------|------|
| GitHub | [pytorch/pytorch](https://github.com/pytorch/pytorch) |
| Stars | ~90,000 |
| Forks | ~24,000 |
| License | BSD-3-Clause |
| Language | Python + C++ |
| Last Update | 2026-04 (very active) |
| Contributors | 4,000+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 95 | Dynamic computation graph, CUDA, MPS, distributed training, TorchScript, torch.compile. Research + production grade. |
| E Ecosystem | 95 | 90k stars, Meta-backed, 4000+ contributors. HuggingFace default. Dominant in research and increasingly in production. |
| M Market | 88 | Won the framework war. Default for LLM training/fine-tuning. Growing production adoption with TorchServe. |
| C Combo | 65 | Python-only. But LLM models trained in PyTorch → served via APIs (vLLM, Ollama) → consumed from TypeScript. Essential knowledge. |
| **Overall** | **86** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 85.8 |

## Core Value
The dominant deep learning framework. Dynamic computation graphs for intuitive debugging. From research prototyping to production deployment. Every major LLM is trained on PyTorch.

## Architecture Highlights
- **Dynamic Computation Graph (Eager Mode)**: Build graph on-the-fly during forward pass
- **torch.compile**: JIT compilation for 2-3x speedup without code changes
- **Distributed Training**: DDP, FSDP for multi-GPU/multi-node training
- **CUDA + MPS**: GPU acceleration for NVIDIA and Apple Silicon
- **TorchScript**: Export models for production (C++ runtime)
- **Ecosystem**: TorchVision, TorchAudio, TorchText, TorchRec

## Key Modules
1. **Autograd Engine** (Core) — Automatic differentiation for all tensor operations
2. **nn Module System** (Core) — Layer definitions, model composition, parameter management
3. **Distributed** (Large) — DDP, FSDP, RPC for multi-GPU/multi-node
4. **torch.compile** (Medium) — Graph capture and optimization
5. **Data Loading** (Medium) — DataLoader, Dataset, DistributedSampler

## Extractable Patterns
- Module composition pattern (nn.Module inheritance)
- Training loop best practices
- Mixed precision training pattern
- Distributed training architecture
