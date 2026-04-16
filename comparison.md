# ML/DL Framework Comparison — 2026-04-16

> Comprehensive comparison of 12 top machine learning, LLM, and AI projects

## Overview Matrix

| Project | Stars | License | Language | TEMC | Category | Status |
|---------|-------|---------|----------|------|----------|--------|
| **HuggingFace Transformers** | 159k | Apache-2.0 | Python | **89** | Model Hub / LLM Framework | 🔴 Essential |
| **Ollama** | 169k | MIT | Go | **89** | Local LLM Runtime | 🔴 Essential |
| **Langfuse** | 8k | MIT/EE | TypeScript | **87** | LLM Observability | 🔴 Essential |
| **LlamaIndex** | 48k | MIT | Python/TS | **86** | RAG Framework | 🔴 Essential |
| **vLLM** | 76k | Apache-2.0 | Python/CUDA | **86** | LLM Serving Engine | 🟡 Important |
| **DSPy** | 22k | MIT | Python | **82** | Prompt Optimization | 🔴 Essential |
| **PyTorch** | 99k | BSD-3 | Python/C++ | **79** | DL Framework | 🟡 Foundation |
| **Haystack** | 18k | Apache-2.0 | Python | **79** | RAG Framework | 🟡 Important |
| **MLflow** | 20k | Apache-2.0 | Python | **76** | ML Experiment Tracking | 🟢 Reference |
| **Streamlit** | — | — | — | — | — (see data-stack) | — |
| **Open Interpreter** | 58k | AGPL-3.0 ⚠️ | Python | **76** | Code Execution Agent | 🟡 Study |
| **Scikit-learn** | 65k | BSD-3 | Python | **73** | Classical ML | 🟢 Reference |
| **TensorFlow** | 194k | Apache-2.0 | C++/Python | **71** | DL Framework | 🟢 Legacy |

## New Category: LLM DevTools

| | DSPy | Langfuse | Haystack | LlamaIndex |
|---|---|---|---|---|
| **Focus** | Prompt optimization | Observability/Evals | Production RAG | Dev-friendly RAG |
| **Paradigm** | Programming | Monitoring | Pipelines | Index/Query |
| **TypeScript** | ❌ Python | ✅ Native | ❌ Python | ✅ LlamaIndex.TS |
| **Best for** | Optimizing LLM calls | Debugging/monitoring | Enterprise RAG | Quick RAG prototypes |
| **License** | MIT ✅ | MIT ✅ | Apache ✅ | MIT ✅ |

## New Category: ML Operations

| | MLflow | Langfuse | Weights & Biases |
|---|---|---|---|
| **Scope** | Full ML lifecycle | LLM-specific | Full ML lifecycle |
| **Self-host** | ✅ Yes | ✅ Yes | ❌ Cloud only |
| **LLM Tracing** | ✅ (2024+) | ✅ Native | ✅ Weave |
| **Open Source** | ✅ Apache | ✅ MIT | ❌ Proprietary |
| **Best for** | Model training ops | LLM app monitoring | Research tracking |

## New Category: AI Agents

| | Open Interpreter | LlamaIndex Agents | DSPy ReAct |
|---|---|---|---|
| **Execution** | Local code | Tool calling | LLM programs |
| **Safety** | ⚠️ Full access | ✅ Sandboxed tools | ✅ Controlled |
| **License** | AGPL ⚠️ | MIT ✅ | MIT ✅ |
| **Best for** | Local automation | Structured tasks | Optimized agents |

## Technology Stack Compatibility (with 天子基准栈)

| Project | TypeScript | Next.js | Supabase | OpenAI | Vercel | Score |
|---------|-----------|---------|----------|--------|--------|-------|
| Langfuse | ✅ Native | ✅ Built on it | ✅ Postgres | ✅ | ✅ | ⭐⭐⭐⭐⭐ |
| LlamaIndex | ✅ LlamaIndex.TS | ✅ | ✅ pgvector | ✅ | ✅ | ⭐⭐⭐⭐⭐ |
| Ollama | ✅ REST API | ✅ | ✅ | ✅ compatible | ❌ local | ⭐⭐⭐⭐ |
| DSPy | ❌ Python | ❌ API only | ✅ | ✅ | ❌ | ⭐⭐ |
| Haystack | ❌ Python | ❌ API only | ✅ pgvector | ✅ | ❌ | ⭐⭐ |
| HF Transformers | ❌ Python | ❌ API only | ✅ | ✅ | ❌ | ⭐⭐⭐ |
| MLflow | ❌ Python | ❌ REST API | ❌ | ✅ | ❌ | ⭐ |
| Open Interpreter | ❌ Python | ❌ | ❌ | ✅ | ❌ | ⭐ |
| vLLM | ❌ Python | ❌ API only | ❌ | ✅ compatible | ❌ | ⭐⭐ |
| PyTorch | ❌ Python | ❌ | ❌ | N/A | ❌ | ⭐ |
| Scikit-learn | ❌ Python | ❌ | ❌ | N/A | ❌ | ⭐ |
| TensorFlow | ✅ TF.js | ✅ | ❌ | N/A | ✅ | ⭐⭐ |

## 天子 Priority Stack (Updated)

```
Layer 5 (Observe):     Langfuse (traces + evals + cost tracking)
Layer 4 (Product):     LlamaIndex.TS + Next.js + Supabase pgvector
Layer 3 (Optimize):    DSPy (prompt optimization via Python API)
Layer 3 (LLM Runtime): Ollama (dev) + OpenAI API (prod) + vLLM (self-host)
Layer 2 (Models):      HuggingFace Transformers (fine-tuning + model hub)
Layer 1 (Foundation):  PyTorch (understanding, not coding)
Layer 0 (Classical):   Scikit-learn (reference only)
```

## Key Insight

> **2026 update**: The stack now has an observability layer (Langfuse) and an optimization layer (DSPy). Building an LLM app without monitoring is like shipping code without logs. Langfuse is built on YOUR stack (Next.js+TS) — study its codebase as a SaaS architecture masterclass.
