[English](README.md) | [中文](README_CN.md)

# 🧠 ml-stack

![Stars](https://img.shields.io/github/stars/bursh3347-collab/ml-stack?style=flat-square)
![License](https://img.shields.io/github/license/bursh3347-collab/ml-stack?style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/bursh3347-collab/ml-stack?style=flat-square)

> ⭐ Maturity: **L1 Growing** — 7 projects analyzed, best practices extracted.

Extracted best practices and deep analysis from **7 top machine learning, deep learning, and LLM open-source projects** on GitHub. Each project is scored using our [TEMC methodology](#temc-scoring) (Technology × Ecosystem × Market × Combo).

## 📊 Dashboard (2026-04-15)

| Metric | Value |
|--------|-------|
| Projects Analyzed | 7 |
| Total Stars Covered | 813,000+ |
| Best Practices Docs | 3 |
| TEMC Score Range | 71-89 |

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

## 📋 What's Inside

### Comparison & Best Practices

- [📊 Full Comparison Table](comparison.md) — Horizontal comparison across all 7 projects
- [🚀 Model Serving Patterns](best-practices/model-serving.md) — OpenAI-compatible APIs, continuous batching, graceful degradation
- [🔍 RAG Patterns](best-practices/rag-patterns.md) — Pipeline design, hybrid search, chunking strategies, evaluation
- [🎯 Fine-Tuning Guide](best-practices/fine-tuning.md) — LoRA/QLoRA, dataset prep, when NOT to fine-tune

## 🎯 Optimal ML Stack for Solo AI SaaS

```
Layer 4 (Product):     LlamaIndex.TS + Next.js + Supabase pgvector
Layer 3 (LLM Runtime): Ollama (dev) + OpenAI API (prod) + vLLM (self-host)
Layer 2 (Models):      HuggingFace Transformers (fine-tuning + model hub)
Layer 1 (Foundation):  PyTorch (understanding, not coding)
```

Work at **Layer 3-4 for maximum ROI**. Only descend to Layer 1-2 when custom models are required for differentiation.

## 🏗️ Repository Structure

```
ml-stack/
├── README.md              ← You are here
├── README_CN.md           ← 中文版
├── projects/              ← Detailed project analyses (TEMC scored)
├── best-practices/        ← Extracted patterns from multiple projects
├── code/                  ← Extractable code (TODO: L2)
├── comparison.md          ← Full horizontal comparison table
└── SOURCES.md             ← All source projects with licenses
```

## <a id="temc-scoring"></a>📊 TEMC Scoring

**TEMC** = Technology × 0.25 + Ecosystem × 0.20 + Market × 0.30 + Combo × 0.25

- **T (Technology)**: Code quality, architecture, tech stack fit, docs
- **E (Ecosystem)**: Stars/forks, community activity, integrations, maintainer reputation
- **M (Market)**: Timing, competitive scarcity, trend alignment, commercializability
- **C (Combo)**: Stack compatibility, modularity, business combo potential, learning cost

## ⚔️ Solo Dev Verdict

**Ollama + LlamaIndex is the killer combo for solo AI SaaS.** Ollama gives you local LLM inference during development (zero API cost), and LlamaIndex.TS provides the entire RAG pipeline in TypeScript — data loading, chunking, indexing, retrieval, and synthesis.

**HuggingFace is your model supermarket.** Don't train from scratch. Browse 500k+ pre-trained models, fine-tune with LoRA if needed, deploy via the Inference API or download to Ollama.

**vLLM is for when you need to self-host at scale.** Continuous batching gives 2-4x throughput over naive serving. But for a solo dev starting out, OpenAI API + Ollama covers 95% of use cases.

**Skip TensorFlow.** PyTorch won the research and startup ecosystem. TensorFlow is legacy unless you're deploying to edge devices with TFLite.

## License

This analysis repository is MIT licensed. Individual projects have their own licenses — see [SOURCES.md](SOURCES.md).
