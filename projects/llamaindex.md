# LlamaIndex

> The data framework for LLM applications — connect custom data to LLMs.

| Metric | Data |
|--------|------|
| GitHub | [run-llama/llama_index](https://github.com/run-llama/llama_index) |
| Stars | ~40,000 |
| Forks | ~6,000 |
| License | MIT |
| Language | Python (TypeScript version: LlamaIndex.TS) |
| Last Update | 2026-04 (very active) |
| Contributors | 1,000+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 85 | Comprehensive RAG framework. 160+ data connectors. Vector stores, knowledge graphs, agents. |
| E Ecosystem | 82 | 40k stars, well-funded startup. LlamaHub connector marketplace. Active community. |
| M Market | 88 | RAG is the #1 LLM application pattern. Every enterprise needs it. Growing rapidly. |
| C Combo | 80 | LlamaIndex.TS exists for TypeScript! MIT license. Direct integration with Tianzi's stack. |
| **Overall** | **85** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 84.8 |

## Core Value
The comprehensive framework for building RAG (Retrieval-Augmented Generation) applications. Connect any data source to LLMs with optimized indexing, retrieval, and response synthesis.

## Architecture Highlights
- **Data Connectors (LlamaHub)**: 160+ connectors for documents, APIs, databases
- **Index Types**: Vector, tree, keyword, knowledge graph, SQL
- **Query Engine**: Natural language → index query → LLM synthesis
- **Agent Framework**: ReAct agents with tools and memory
- **Evaluation**: Built-in RAG evaluation metrics (faithfulness, relevancy)
- **LlamaIndex.TS**: TypeScript version for Node.js/Next.js

## Key Modules
1. **Data Ingestion** (Large) — Document loaders, chunking, metadata extraction
2. **Index Engine** (Core) — Vector store, tree, knowledge graph indexes
3. **Query Engine** (Core) — Retrieval, reranking, response synthesis
4. **Agent System** (Medium) — ReAct, OpenAI function calling agents
5. **Evaluation** (Small) — Faithfulness, relevancy, context metrics

## Extractable Patterns
- **⭐ Universal Code Candidate: RAG Pipeline Architecture** → code-base/ai-integration/rag/
- **⭐ Universal Code Candidate: Document Chunking Strategies** → code-base/ai-integration/chunking/
- Knowledge graph + vector hybrid retrieval
- RAG evaluation metrics

## Why High Priority for Tianzi
- LlamaIndex.TS = TypeScript native RAG
- MIT license = fully commercial
- RAG is core technology for AI knowledge SaaS
- 160+ connectors = rapid data integration
