[English](README.md) | [中文](README_CN.md)

# 🧠 ml-stack

![Stars](https://img.shields.io/github/stars/bursh3347-collab/ml-stack?style=flat-square)
![License](https://img.shields.io/github/license/bursh3347-collab/ml-stack?style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/bursh3347-collab/ml-stack?style=flat-square)

> ⭐ Maturity: **L2 Growing** — 18 projects analyzed, best practices extracted, code extraction starting.

Extracted best practices and deep analysis from **18 top machine learning, deep learning, and LLM open-source projects** on GitHub. Each project is scored using our [TEMC methodology](#temc-scoring) (Technology × Ecosystem × Market × Combo).

## 📊 Dashboard (2026-04-16)

| Metric | Value |
|--------|-------|
| Projects Analyzed | 18 |
| Total Stars Covered | 1,200,000+ |
| Best Practices Docs | 3 |
| TEMC Score Range | 70-89 |

## 🏆 Project Rankings by TEMC Score

| Rank | Project | Stars | TEMC | Priority |
|------|---------|-------|------|----------|
| 1 | [HuggingFace Transformers](projects/huggingface-transformers.md) | 159k | **89** | 🔴 Essential |
| 1 | [Ollama](projects/ollama.md) | 169k | **89** | 🔴 Essential |
| 3 | [Langfuse](projects/langfuse.md) | 8k | **87** | 🔴 Essential |
| 4 | [LlamaIndex](projects/llamaindex.md) | 48k | **86** | 🔴 Essential |
| 4 | [vLLM](projects/vllm.md) | 76k | **86** | 🟡 Important |
| 6 | [LangChain](projects/langchain.md) | 100k | **83** | 🟡 Important |
| 7 | [DSPy](projects/dspy.md) | 22k | **82** | 🟡 Important |
| 8 | [Stable Diffusion](projects/stable-diffusion.md) | 69k | **79** | 🟡 Important |
| 8 | [PyTorch](projects/pytorch.md) | 99k | **79** | 🟡 Foundation |
| 8 | [Haystack](projects/haystack.md) | 18k | **79** | 🟡 Important |
| 11 | [Ray](projects/ray.md) | 35k | **77** | 🟢 Reference |
| 12 | [MLflow](projects/mlflow.md) | 20k | **76** | 🟢 Reference |
| 12 | [Open Interpreter](projects/open-interpreter.md) | 58k | **76** | 🟢 Reference |
| 14 | [W&B (wandb)](projects/wandb.md) | 10k | **75** | 🟢 Reference |
| 15 | [Scikit-learn](projects/scikit-learn.md) | 65k | **73** | 🟢 Reference |
| 16 | [ONNX Runtime](projects/onnx-runtime.md) | 15k | **72** | 🟢 Infra |
| 17 | [TensorFlow](projects/tensorflow.md) | 194k | **71** | 🟢 Legacy |
| 18 | [JAX](projects/jax.md) | 32k | **70** | 🟢 Research |

## 📋 What's Inside

### Comparison & Best Practices

- [📊 Full Comparison Table](comparison.md) — Horizontal comparison across all projects
- [🚀 Model Serving Patterns](best-practices/model-serving.md) — OpenAI-compatible APIs, continuous batching, graceful degradation
- [🔍 RAG Patterns](best-practices/rag-patterns.md) — Pipeline design, hybrid search, chunking strategies, evaluation
- [🎯 Fine-Tuning Guide](best-practices/fine-tuning.md) — LoRA/QLoRA, dataset prep, when NOT to fine-tune

### Project Categories

**🔴 Core Stack (TEMC ≥ 83)**
- HuggingFace Transformers — Model hub & fine-tuning
- Ollama — Local LLM inference
- Langfuse — LLM observability
- LlamaIndex — RAG framework
- vLLM — Production LLM serving
- LangChain — LLM application framework

**🟡 Important Tools (TEMC 75-82)**
- DSPy — Programmatic prompt optimization
- Stable Diffusion — Image generation
- PyTorch — Deep learning foundation
- Haystack — Production NLP pipelines
- Ray — Distributed compute
- MLflow — ML experiment tracking

**🟢 Reference & Specialized (TEMC < 75)**
- Open Interpreter, W&B, Scikit-learn, ONNX Runtime, TensorFlow, JAX

## 🎯 Optimal ML Stack for Solo AI SaaS

```
Layer 5 (Image):       Stable Diffusion / Flux (via Replicate API)
Layer 4 (Product):     LlamaIndex.TS + Next.js + Supabase pgvector
Layer 3 (LLM Runtime): Ollama (dev) + OpenAI API (prod) + vLLM (self-host)
Layer 2 (Models):      HuggingFace Transformers (fine-tuning + model hub)
Layer 1 (Foundation):  PyTorch (understanding, not coding)
Layer 0 (Scale):       Ray (when distributed compute needed)
```

Work at **Layer 3-5 for maximum ROI**. Only descend to Layer 0-2 when custom models are required for differentiation.

## 📈 Surge Board (Week of 2026-04-16)

| Rank | Project | Total Stars | Weekly Δ | Trend |
|------|---------|-------------|----------|-------|
| 1 | Ollama | 169k | +2.1k | 🚀 |
| 2 | LangChain | 100k | +800 | ↑ |
| 3 | vLLM | 76k | +600 | ↑ |
| 4 | Stable Diffusion | 69k | +200 | → |
| 5 | LlamaIndex | 48k | +400 | ↑ |

## 🏗️ Repository Structure

```
ml-stack/
├── README.md              ← You are here
├── README_CN.md           ← 中文版
├── projects/              ← 18 detailed project analyses (TEMC scored)
├── best-practices/        ← Extracted patterns from multiple projects
├── code/                  ← Extractable code (TODO: L2→L3)
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

**LangChain is the Swiss Army knife.** 100+ LLM integrations and the largest ecosystem, but criticized for over-abstraction. Use for prototyping, consider lighter alternatives for production.

**HuggingFace is your model supermarket.** Don't train from scratch. Browse 500k+ pre-trained models, fine-tune with LoRA if needed, deploy via the Inference API or download to Ollama.

**Stable Diffusion unlocks image generation SaaS.** Self-host via Replicate/RunPod for zero infra management. Fine-tune with LoRA for customer-specific models. Build value in workflow/UX, not the model.

**Ray + ONNX Runtime are for scale.** Bookmark them — you'll need Ray when going multi-GPU and ONNX Runtime when optimizing inference cost. Not relevant at MVP stage.

**JAX is for ideas, not products.** Study the composable transformation design (jit/grad/vmap) to become a better ML engineer, but build products with PyTorch or API-based LLMs.

## License

This analysis repository is MIT licensed. Individual projects have their own licenses — see [SOURCES.md](SOURCES.md).
