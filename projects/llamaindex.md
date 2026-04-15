# LlamaIndex

> The leading document agent and OCR platform — connect LLMs to your data.

| Metric | Data |
|--------|------|
| GitHub | https://github.com/run-llama/llama_index |
| Stars | 48,608 |
| Forks | 7,198 |
| License | MIT |
| Language | Python (+ TypeScript version) |
| Last Commit | 2026-04-15 (today) |
| Open Issues | 287 |

## TEMC Scoring

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 82 | Good abstraction for RAG pipelines, document agents, OCR. Modular connector system. Supports 160+ data sources. TypeScript version (LlamaIndex.TS) available! |
| E (Ecosystem) | 80 | 48k stars, 7k forks. Active community. LlamaCloud (managed service). Regular releases. Good docs. |
| M (Market) | 88 | RAG is THE use case for enterprise AI. Document understanding + agent + OCR = critical stack. Perfect market timing. |
| C (Combo) | 85 | **TypeScript version available** = directly matches天子's baseline stack. MIT license. RAG patterns essential for any AI SaaS. Low learning cost for TS version. |
| **Composite** | **84** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Analysis

```
llama_index/
├── llama-index-core/       # Core framework
│   ├── indices/            # Index types (vector, tree, keyword)
│   ├── query_engine/       # Query processing
│   ├── agent/              # Agent framework
│   ├── retrievers/         # Retrieval strategies
│   └── storage/            # Storage backends
├── llama-index-integrations/  # 160+ integrations
│   ├── llms/               # LLM providers
│   ├── embeddings/         # Embedding providers
│   ├── vector_stores/      # Vector DB connectors
│   └── readers/            # Data source readers
└── llama-index-packs/      # Pre-built RAG recipes
```

**Architecture Pattern**: Plugin-based, monorepo with separate packages, connector pattern.

## Core Modules

1. **Index/Retriever** — Vector/keyword/tree index with hybrid search (medium, medium coupling)
2. **Query Engine** — Transform queries and synthesize responses (medium, medium coupling)
3. **Agent Framework** — Tool-using agents with memory (medium, low coupling)
4. **Data Connectors** — 160+ data source readers (small each, low coupling)
5. **Storage** — Persistence layer for indices (medium, low coupling)

## Extractable Components

| Module | Difficulty | Est. Time | Target |
|--------|-----------|-----------|--------|
| RAG pipeline patterns | Simple copy | 2-4h | code-base/ai-integration/rag/ |
| Vector store abstraction | Need adaptation | 4h | code-base/database/ |
| Agent tool patterns | Need adaptation | 4h | code-base/ai-integration/ |
| Document parsing pipeline | Need adaptation | 6h | code-base/ai-integration/ |

⭐ **Universal Code Candidate**: RAG pipeline pattern, vector store abstraction, document parsing.

## Business Value

- **Pain Point**: Connecting LLMs to custom data (致命级 for enterprise AI)
- **TAM**: RAG/Document AI market $15B+ by 2027
- **Monetization**: LlamaCloud ($200/mo+). For天子: build RAG-powered Micro SaaS.
- **Differentiation**: Niche vertical RAG (legal, medical, financial document AI).

## Why It Might NOT Be Worth Deep Investment

- 🟡 TypeScript version lags behind Python version in features
- 🟡 LlamaCloud competes with self-hosted deployments
- 🟡 RAG market getting crowded (LangChain, Haystack, etc.)
- ✅ MIT license + TypeScript version = perfect for天子
- ✅ Best RAG abstraction layer available
