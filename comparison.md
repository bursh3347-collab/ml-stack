# Machine Learning & Deep Learning — Comparison

> Last updated: 2026-04-15

## Overview Matrix

| Project | Stars | Language | License | Type | TEMC | Best For |
|---------|-------|----------|---------|------|------|----------|
| **TensorFlow** | ~190k | Python/C++ | Apache-2.0 | DL Framework | 75 | Production ML, mobile/edge |
| **HuggingFace** | ~145k | Python | Apache-2.0 | Model Hub | **88** | Pretrained models, NLP/LLM |
| **Ollama** | ~120k | Go | MIT | Local LLM | **90** | Running LLMs locally |
| **Puppeteer** | ~94k | TypeScript | Apache-2.0 | Browser Auto | — | (see automation-stack) |
| **PyTorch** | ~90k | Python/C++ | BSD-3 | DL Framework | **86** | Deep learning research + prod |
| **Scikit-learn** | ~62k | Python | BSD-3 | Classical ML | 73 | Tabular data, preprocessing |
| **vLLM** | ~50k | Python/CUDA | Apache-2.0 | LLM Inference | **84** | Production LLM serving |
| **LlamaIndex** | ~40k | Python/TS | MIT | RAG Framework | **85** | RAG applications |
| **W&B** | ~10k | Python | MIT | MLOps | 77 | Experiment tracking |

## Category Breakdown

### 🧠 Deep Learning Frameworks
| | PyTorch | TensorFlow |
|---|---------|------------|
| Research Adoption | ★★★★★ | ★★★ |
| Production | ★★★★ | ★★★★★ |
| Dynamic Graph | ✅ | ✅ (TF 2.x) |
| Mobile/Edge | ✅ ExecuTorch | ✅ TFLite (stronger) |
| Community | Growing | Declining |
| **Verdict** | 🏆 **Default choice** | Production legacy |

### 🤖 LLM Infrastructure
| | Ollama | vLLM | HuggingFace TGI |
|---|--------|------|------------------|
| Use Case | Local dev | Production serving | Production serving |
| Ease of Use | ★★★★★ | ★★★ | ★★★ |
| Performance | Good | ★★★★★ (PagedAttention) | ★★★★ |
| API | OpenAI-compatible | OpenAI-compatible | Custom |
| Multi-GPU | Limited | ✅ Tensor parallel | ✅ |
| **Verdict** | 🏆 **Local dev** | 🏆 **Production** | Alternative |

### 📚 RAG & LLM Applications
| | LlamaIndex | LangChain |
|---|-----------|----------|
| Focus | Data framework | Agent framework |
| TypeScript | ✅ LlamaIndex.TS | ✅ LangChain.js |
| Data Connectors | 160+ | 80+ |
| RAG Quality | ★★★★★ | ★★★★ |
| Agent Support | Good | ★★★★★ |
| **Verdict** | 🏆 **For RAG** | Better for agents |

## Recommendation for Tianzi (TypeScript + Next.js + AI)

1. **Ollama** (TEMC 90) — #1 pick. Local LLM for development. OpenAI-compatible API. MIT.
2. **HuggingFace** (TEMC 88) — #2. Gateway to all models. Essential knowledge.
3. **PyTorch** (TEMC 86) — #3. Understand model training. Essential ML foundation.
4. **LlamaIndex** (TEMC 85) — #4. RAG framework with TypeScript version. Direct use.
5. **vLLM** (TEMC 84) — Production LLM serving when you need scale.
6. **W&B** (TEMC 77) — Experiment tracking, eval concepts.
7. **TensorFlow** (TEMC 75) / **Scikit-learn** (TEMC 73) — Reference, lower priority.
