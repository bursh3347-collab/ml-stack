# ML/DL Framework Comparison — 2026-04-15

> Comprehensive comparison of 7 top machine learning and deep learning projects

## Overview Matrix

| Project | Stars | License | Language | TEMC | Category | Status |
|---------|-------|---------|----------|------|----------|--------|
| **HuggingFace Transformers** | 159k | Apache-2.0 | Python | **89** | Model Hub / LLM Framework | 🔴 Essential |
| **Ollama** | 169k | MIT | Go | **89** | Local LLM Runtime | 🔴 Essential |
| **LlamaIndex** | 48k | MIT | Python/TS | **86** | RAG Framework | 🔴 Essential |
| **vLLM** | 76k | Apache-2.0 | Python/CUDA | **86** | LLM Serving Engine | 🟡 Important |
| **PyTorch** | 99k | BSD-3 | Python/C++ | **79** | DL Framework | 🟡 Foundation |
| **Scikit-learn** | 65k | BSD-3 | Python | **73** | Classical ML | 🟢 Reference |
| **TensorFlow** | 194k | Apache-2.0 | C++/Python | **71** | DL Framework | 🟢 Legacy |

## Technology Stack Compatibility (with 天子基准栈)

| Project | TypeScript | Next.js | Supabase | OpenAI | Vercel | Score |
|---------|-----------|---------|----------|--------|--------|-------|
| LlamaIndex | ✅ LlamaIndex.TS | ✅ | ✅ pgvector | ✅ | ✅ | ⭐⭐⭐⭐⭐ |
| Ollama | ✅ REST API | ✅ | ✅ | ✅ compatible | ❌ local | ⭐⭐⭐⭐ |
| HF Transformers | ❌ Python | ❌ API only | ✅ | ✅ | ❌ | ⭐⭐⭐ |
| vLLM | ❌ Python | ❌ API only | ❌ | ✅ compatible | ❌ | ⭐⭐ |
| PyTorch | ❌ Python | ❌ | ❌ | N/A | ❌ | ⭐ |
| Scikit-learn | ❌ Python | ❌ | ❌ | N/A | ❌ | ⭐ |
| TensorFlow | ✅ TF.js | ✅ | ❌ | N/A | ✅ | ⭐⭐ |

## Activity & Health (2026-04-15)

| Project | Last Commit | Commits/Day | Open Issues | Issue Ratio | Release Freq |
|---------|------------|-------------|-------------|-------------|-------------|
| PyTorch | Today | 20+ | 18,530 | High volume | Monthly |
| vLLM | Today | 15+ | 4,279 | High volume | Bi-weekly |
| HF Transformers | Today | 10+ | 2,349 | Well managed | Monthly |
| Ollama | Today | 5+ | 2,943 | Active | Weekly |
| LlamaIndex | Today | 5+ | 287 | Well managed | Bi-weekly |
| Scikit-learn | Today | 3+ | 2,041 | Stable | Quarterly |
| TensorFlow | Today | 5+ | 4,417 | Stable | Quarterly |

## Use Case Mapping

| Use Case | Best Choice | Alternative | Notes |
|----------|------------|-------------|-------|
| **Build RAG SaaS** | LlamaIndex.TS | LangChain.js | TypeScript native |
| **Local LLM dev** | Ollama | llama.cpp | Docker-like UX |
| **Fine-tune models** | HF Transformers | Axolotl | PEFT/LoRA support |
| **Serve LLMs at scale** | vLLM | TGI (HF) | PagedAttention |
| **Custom model training** | PyTorch | JAX | Research standard |
| **Tabular ML** | Scikit-learn | XGBoost | Gold standard API |
| **Browser ML** | TensorFlow.js | ONNX Runtime Web | Client-side inference |

## 天子 Priority Stack

```
Layer 4 (Product):     LlamaIndex.TS + Next.js + Supabase pgvector
Layer 3 (LLM Runtime): Ollama (dev) + OpenAI API (prod) + vLLM (self-host)
Layer 2 (Models):      HuggingFace Transformers (fine-tuning + model hub)
Layer 1 (Foundation):  PyTorch (understanding, not coding)
Layer 0 (Classical):   Scikit-learn (reference only)
```

## Key Insight

> **For a one-person AI SaaS company, the optimal strategy is to work at Layer 3-4 (LlamaIndex + Ollama + OpenAI) and only descend to Layer 1-2 (PyTorch + HF) when building custom models is required for differentiation.**
