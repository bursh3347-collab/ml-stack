# 🧠 ML Stack

> ⭐ Maturity: **L1 Growing** — 7 projects analyzed, best practices extracted

Extracted best practices and analysis from the top machine learning and deep learning open-source projects. Part of the [GitHub Open Source Knowledge Reorganization Project](https://github.com/bursh3347-collab).

## 📈 Dashboard (2026-04-15)

| Metric | Value |
|--------|-------|
| Projects Analyzed | 7 |
| Total Stars Covered | 813,000+ |
| Best Practices Docs | 3 |
| TEMC Score Range | 71-89 |
| Last Updated | 2026-04-15 |

## 🏆 Project Rankings by TEMC Score

| Rank | Project | Stars | TEMC | Priority |
|------|---------|-------|------|----------|
| 1 | [HuggingFace Transformers](projects/huggingface-transformers.md) | 159k | **89** | 🔴 Essential |
| 1 | [Ollama](projects/ollama.md) | 169k | **89** | 🔴 Essential |
| 3 | [LlamaIndex](projects/llamaindex.md) | 48k | **86** | 🔴 Essential |
| 3 | [vLLM](projects/vllm.md) | 76k | **86** | 🟡 Important |
| 5 | [PyTorch](projects/pytorch.md) | 99k | **79** | 🟡 Foundation |
| 6 | [Scikit-learn](projects/scikit-learn.md) | 65k | **73** | 🟢 Reference |
| 7 | [TensorFlow](projects/tensorflow.md) | 194k | **71** | 🟢 Legacy |

## 📂 Repository Structure

```
ml-stack/
├── README.md              ← You are here
├── projects/              ← Detailed project analyses (TEMC scored)
│   ├── pytorch.md
│   ├── tensorflow.md
│   ├── huggingface-transformers.md
│   ├── ollama.md
│   ├── llamaindex.md
│   ├── vllm.md
│   └── scikit-learn.md
├── best-practices/        ← Extracted patterns from multiple projects
│   ├── model-serving.md   ← OpenAI-compatible API, continuous batching
│   ├── rag-patterns.md    ← RAG pipeline, hybrid search, chunking
│   └── fine-tuning.md     ← LoRA, QLoRA, dataset prep, evaluation
├── code/                  ← Extractable code (TODO: L2)
├── comparison.md          ← Full horizontal comparison table
└── SOURCES.md             ← All source projects with licenses
```

## 🎯 Key Insight

For a **one-person AI SaaS company**, the optimal ML stack is:

```
Layer 4 (Product):     LlamaIndex.TS + Next.js + Supabase pgvector
Layer 3 (LLM Runtime): Ollama (dev) + OpenAI API (prod) + vLLM (self-host)
Layer 2 (Models):      HuggingFace Transformers (fine-tuning + model hub)
Layer 1 (Foundation):  PyTorch (understanding, not coding)
```

Work at Layer 3-4 for maximum ROI. Only descend to Layer 1-2 when custom models are required for differentiation.

## 🔧 Best Practices

- [Model Serving Patterns](best-practices/model-serving.md) — OpenAI-compatible APIs, continuous batching, graceful degradation
- [RAG Patterns](best-practices/rag-patterns.md) — Pipeline design, hybrid search, chunking strategies, evaluation
- [Fine-Tuning Guide](best-practices/fine-tuning.md) — LoRA/QLoRA, dataset prep, when NOT to fine-tune

## 📊 [Full Comparison Table](comparison.md)

See detailed horizontal comparison across all 7 projects.

## License

This analysis repository is MIT licensed. Individual projects have their own licenses — see [SOURCES.md](SOURCES.md).
