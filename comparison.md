# ML/DL Stack — Project Comparison

> Horizontal comparison of 7 high-star ML/DL projects analyzed in this repository.

*Last updated: 2026-04-15*

## Overview Table

| Project | Stars | License | Language | Latest | T | E | M | C | **TEMC** |
|---------|-------|---------|----------|--------|---|---|---|---|----------|
| **HF Transformers** | 159k | Apache-2.0 | Python | v5.5.4 (Apr 13) | 90 | 95 | 85 | 82 | **88** |
| **Ollama** | 169k | MIT | Go | — | 85 | 92 | 90 | 85 | **88** |
| **vLLM** | 77k | Apache-2.0 | Python/C++ | v0.19.0 (Apr 3) | 90 | 88 | 92 | 78 | **87** |
| **LlamaIndex** | 49k | MIT | Python/TS | — | 82 | 80 | 88 | 85 | **84** |
| **PyTorch** | 99k | BSD-3 | Python/C++ | v2.11.0 (Mar 23) | 92 | 95 | 75 | 70 | **82** |
| **TensorFlow** | 195k | Apache-2.0 | C++/Python | — | 88 | 90 | 65 | 60 | **75** |
| **Scikit-learn** | 66k | BSD-3 | Python | — | 88 | 85 | 60 | 65 | **73** |

## Category Breakdown

### 🏗️ Frameworks (Foundation Layer)
| | PyTorch | TensorFlow |
|---|---------|------------|
| **Position** | #1 in research + gaining production | #1 in legacy production |
| **Growth** | Accelerating | Decelerating |
| **TypeScript** | ❌ | TF.js (limited) |
| **Best For** | Training, research, new projects | Enterprise legacy, TPU, mobile (TFLite) |
| **Recommendation** | ✅ Learn this | 🟡 Know architecture, don't invest deeply |

### 🧠 Model Hub & Inference
| | HF Transformers | Ollama | vLLM |
|---|-----------------|--------|------|
| **Position** | Universal model hub | Local LLM runner | Production serving |
| **Use Case** | Model access & fine-tuning | Development & privacy | High-throughput serving |
| **API** | Python library | OpenAI-compatible REST | OpenAI-compatible REST |
| **TypeScript** | transformers.js | API (language-agnostic) | API (language-agnostic) |
| **Best For** | Any LLM application | Local dev, privacy-first apps | Production deployment |
| **Recommendation** | ✅ Essential | ✅ Essential for local dev | ✅ Essential for deployment |

### 📊 Data & RAG
| | LlamaIndex | Scikit-learn |
|---|------------|-------------|
| **Position** | #1 RAG framework | #1 classical ML |
| **Growth** | Strong growth | Stable/mature |
| **TypeScript** | ✅ LlamaIndex.TS! | ❌ |
| **Best For** | RAG, document AI, agents | Preprocessing, tabular ML |
| **Recommendation** | ✅ High priority (TS version!) | 🟡 Know basics |

## Stack Recommendation for天子

### Must-Have (directly usable)
1. **Ollama** — Local LLM for development (88 TEMC)
2. **HF Transformers** — Model access for any AI product (88 TEMC)
3. **LlamaIndex** — RAG pipeline, TypeScript version available (84 TEMC)

### Should-Know (architecture understanding)
4. **vLLM** — Production LLM serving patterns (87 TEMC)
5. **PyTorch** — Foundation of all AI (82 TEMC)

### Nice-to-Know (reference only)
6. **TensorFlow** — Legacy reference, TF.js for browser ML (75 TEMC)
7. **Scikit-learn** — API design gold standard (73 TEMC)

## Key Insight

> The real value for a one-person Micro SaaS operation is in the **application layer** (Ollama + HF + LlamaIndex), not the **framework layer** (PyTorch/TF). Master the tools that let you ship products, not the ones that let you train models from scratch.
