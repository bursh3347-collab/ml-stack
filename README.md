# 🧠 ml-stack

> ⭐ Maturity: **L1 Growing** — 8 projects analyzed, comparison and best practices available.

Extracted best practices and deep analyses from the world's top machine learning & deep learning open-source projects.

## 📊 Leaderboard (by TEMC Score)

| Rank | Project | Stars | TEMC | Trend |
|------|---------|-------|------|-------|
| 1 | [Ollama](projects/ollama.md) | ~120k | **90** | 🚀 |
| 2 | [HuggingFace Transformers](projects/huggingface-transformers.md) | ~145k | **88** | 🚀 |
| 3 | [PyTorch](projects/pytorch.md) | ~90k | **86** | ↑ |
| 4 | [LlamaIndex](projects/llamaindex.md) | ~40k | **85** | 🚀 |
| 5 | [vLLM](projects/vllm.md) | ~50k | **84** | 🚀 |
| 6 | [W&B](projects/wandb.md) | ~10k | **77** | ↑ |
| 7 | [TensorFlow](projects/tensorflow.md) | ~190k | **75** | → |
| 8 | [Scikit-learn](projects/scikit-learn.md) | ~62k | **73** | → |

## 📂 Repository Structure

```
ml-stack/
├── README.md              ← You are here
├── projects/              ← Individual project analyses (TEMC-scored)
│   ├── pytorch.md
│   ├── tensorflow.md
│   ├── huggingface-transformers.md
│   ├── ollama.md
│   ├── llamaindex.md
│   ├── vllm.md
│   ├── wandb.md
│   └── scikit-learn.md
├── best-practices/        ← Extracted patterns
│   ├── model-serving.md
│   ├── rag-patterns.md
│   └── fine-tuning.md
├── code/                  ← Extracted code (coming in L2)
├── comparison.md          ← Side-by-side comparison table
└── SOURCES.md             ← All source projects with links
```

## 🔥 Quick Picks

- **Running LLMs locally?** → [Ollama](projects/ollama.md) — Docker for LLMs, OpenAI-compatible API
- **Need pretrained models?** → [HuggingFace](projects/huggingface-transformers.md) — The npm of ML
- **Building RAG apps?** → [LlamaIndex](projects/llamaindex.md) — TypeScript version available!
- **Production LLM serving?** → [vLLM](projects/vllm.md) — PagedAttention for 24x throughput
- **Learning deep learning?** → [PyTorch](projects/pytorch.md) — The framework standard

## 📖 Best Practices

- [Model Serving](best-practices/model-serving.md) — Deployment patterns from vLLM, Ollama, TF Serving
- [RAG Patterns](best-practices/rag-patterns.md) — Retrieval-Augmented Generation architecture
- [Fine-Tuning](best-practices/fine-tuning.md) — LoRA, data preparation, evaluation

---

*Part of the [GitHub Open Source Knowledge Restructuring Project](https://github.com/bursh3347-collab). Powered by TEMC scoring methodology.*
