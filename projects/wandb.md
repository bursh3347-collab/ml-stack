# Weights & Biases (wandb)

> The AI developer platform — experiment tracking, model management, and MLOps.

| Metric | Data |
|--------|------|
| GitHub | [wandb/wandb](https://github.com/wandb/wandb) |
| Stars | ~10,000 |
| Forks | ~800 |
| License | MIT |
| Language | Python |
| Last Update | 2026-04 (very active) |
| Contributors | 200+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 85 | Experiment tracking, model registry, dataset versioning, hyperparameter sweeps, LLM tracing. |
| E Ecosystem | 80 | 10k stars but massive paid adoption. Used by OpenAI, Meta, NVIDIA. $1.5B+ valuation. |
| M Market | 82 | MLOps market growing. Essential for any serious ML team. LLM evaluation features expanding. |
| C Combo | 62 | Python-only SDK. But concepts (experiment tracking, eval) applicable to any AI app. |
| **Overall** | **77** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 77.3 |

## Core Value
The GitHub for ML experiments. Track every experiment, compare runs, share results. From training metrics to LLM evaluation traces. Used by the world's top AI labs.

## Architecture Highlights
- **Experiment Tracking**: Auto-log metrics, config, code, environment for every run
- **Artifacts**: Version datasets, models, and any file with lineage tracking
- **Sweeps**: Bayesian hyperparameter optimization
- **Tables**: Interactive data exploration and comparison
- **Weave**: LLM tracing and evaluation framework
- **Reports**: Collaborative notebooks with embedded charts

## Extractable Patterns
- Experiment tracking metadata schema
- Artifact versioning with lineage
- LLM evaluation/tracing patterns (Weave)
- Sweep/hyperparameter optimization strategies
