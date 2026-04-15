# LlamaIndex

> The leading document agent and OCR platform — LLM data framework for RAG

| Metric | Data |
|------|------|
| GitHub | https://github.com/run-llama/llama_index |
| Stars | 48,609 |
| Forks | 7,198 |
| License | MIT |
| Language | Python (TypeScript version available) |
| Last Updated | 2026-04-15 |
| Open Issues | 287 |
| Created | 2022-11-02 |

## TEMC Scoring

| Dimension | Score | Rationale |
|------|------|------|
| T (Tech) | 85 | Excellent RAG framework. Data connectors (160+), indexing strategies (vector/keyword/graph/tree), query engines, agent capabilities. TypeScript version (LlamaIndex.TS) matches 天子基准栈. |
| E (Ecosystem) | 82 | 48k stars, 7k forks. Active community and strong corporate backing. Integrations with every major LLM, vector DB, and data source. LlamaHub for community connectors. |
| M (Market) | 88 | RAG is THE #1 LLM application pattern. Every enterprise AI project needs data retrieval. Pivot to "document agent + OCR" expands TAM. |
| C (Combo) | 88 | MIT license! TypeScript version directly fits 天子基准栈 (Next.js). Combines with Ollama for local RAG, OpenAI for cloud RAG. Perfect for AI knowledge SaaS. |
| **Composite** | **86** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value
LlamaIndex is the go-to framework for building RAG (Retrieval-Augmented Generation) applications. It provides the full pipeline: data ingestion → indexing → querying → response synthesis. Its TypeScript version makes it directly usable in 天子's Next.js stack.

## Architecture Highlights
- **Data Connectors**: 160+ connectors (PDF, web, DB, API, S3, Notion, Slack...)
- **Index Types**: VectorStoreIndex, SummaryIndex, KnowledgeGraphIndex, TreeIndex
- **Query Engine**: Retriever + response synthesizer with citations
- **Agent Framework**: Multi-agent orchestration, tool use, function calling
- **LlamaIndex.TS**: Full TypeScript port for Next.js/Node.js applications
- **LlamaParse**: Document parsing/OCR service (commercial product)

## Key Modules
1. **Data Connectors (LlamaHub)** — 160+ data source integrations (large, independent)
2. **Index/Vector Store** — Indexing and storage abstraction (medium, core)
3. **Query Engine** — Retrieval + synthesis pipeline (medium, core)
4. **Agent Framework** — Multi-agent with tool use (medium, growing)
5. **LlamaIndex.TS** — TypeScript port (separate package, independent)

## Extractable Patterns
- ⭐ **通用代码候选**: RAG pipeline pattern (ingest → index → query → synthesize) → code-base/ai-integration/rag/
- ⭐ **通用代码候选**: Data connector abstraction pattern → code-base/ai-integration/data-connectors/
- Vector store integration patterns (Qdrant, Pinecone, ChromaDB)
- Citation/source tracking in LLM responses

## Business Value
- **Pain Point**: Making LLMs work with private/custom data (Critical)
- **Target Users**: Enterprises needing AI over their documents, knowledge workers
- **Monetization**: Knowledge base SaaS, document Q&A, AI search products
- **差异化窗口**: TypeScript version allows full-stack JS RAG SaaS

## Why It Might NOT Be Worth It (反证)
- RAG space is extremely competitive (LangChain, Haystack, DSPy)
- LlamaParse (their commercial product) is what generates revenue, not the open-source framework
- Vector DB landscape is consolidating — integration choices may become obsolete
- Simple RAG patterns can be built with just OpenAI + a vector DB without a framework

## 天子 Verdict
🔴 **HIGH PRIORITY** — LlamaIndex is a cornerstone of 天子's AI knowledge SaaS strategy. The TypeScript version directly fits the基准技术栈. Combine with Supabase pgvector for a full Next.js RAG application. Estimated integration time: 4-8 hours for basic RAG pipeline.
