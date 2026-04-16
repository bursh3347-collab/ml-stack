# Haystack

> Production-ready RAG framework — modular pipelines for LLM applications

| Metric | Value |
|--------|-------|
| GitHub | [deepset-ai/haystack](https://github.com/deepset-ai/haystack) |
| Stars | ~18,000 |
| License | Apache-2.0 ✅ |
| Language | Python |
| Last Update | Active (daily commits) |
| Company | deepset (Berlin, $30M+ funded) |

## TEMC Scores

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 85 | Excellent modular pipeline design. Components are independent, composable, typed. Haystack 2.0 was a ground-up rewrite |
| E (Eco) | 80 | 18k stars, deepset company backing, active community. 100+ integrations via haystack-integrations repo |
| M (Market) | 82 | RAG is THE 2026 enterprise use case. Haystack is the most production-focused RAG framework (vs LlamaIndex = dev-focused) |
| C (Combo) | 68 | Python-native, REST API via Hayhooks. Limited TS integration but pipeline patterns are highly transferable |
| **Composite** | **79** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value

Haystack is the **enterprise-grade RAG framework**. While LlamaIndex is great for prototyping, Haystack excels at production pipelines: document preprocessing → embedding → retrieval → generation, with every step swappable and testable. Haystack 2.0 (2024 rewrite) introduced a clean `Pipeline` → `Component` architecture.

## Architecture Highlights

- **Component** — self-contained units with typed inputs/outputs
- **Pipeline** — DAG of connected components, supports branching/loops
- **Document Stores** — Qdrant, Weaviate, Pinecone, Elasticsearch, pgvector
- **Generators** — OpenAI, Anthropic, Cohere, HuggingFace, Ollama
- **Preprocessors** — file converters, text splitters, cleaners
- **Evaluators** — built-in RAG evaluation metrics

## Solo Dev Verdict

**🟢 HIGH VALUE** — If you're building RAG features, study Haystack's pipeline architecture. The Component pattern (typed I/O, independent, composable) is the gold standard for production RAG. Use it as Python backend or study patterns for TS reimplementation.

## Why It Might NOT Be Worth It

- Python-only (no TypeScript SDK)
- Heavier than LlamaIndex for quick prototypes
- deepset's commercial focus (deepset Cloud) may bias open-source priorities
- Haystack 2.0 breaking changes mean some community resources are outdated
