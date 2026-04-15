# Best Practices: RAG Patterns

> Extracted from LlamaIndex, HuggingFace Transformers, and production RAG deployments

## Overview

Retrieval-Augmented Generation (RAG) is the #1 pattern for making LLMs work with private data. This document captures production-proven patterns from the top RAG frameworks.

## Pattern 1: Basic RAG Pipeline (from LlamaIndex)

**Source**: LlamaIndex (48k⭐, MIT)

```
Documents → Chunking → Embedding → Vector Store → Query → Retrieval → LLM → Response
```

**TypeScript Implementation** (LlamaIndex.TS + Supabase):
```typescript
import { VectorStoreIndex, SimpleDirectoryReader } from 'llamaindex';
import { SupabaseVectorStore } from '@llamaindex/community';

// 1. Ingest
const documents = await new SimpleDirectoryReader().loadData('./docs');

// 2. Index (with Supabase pgvector)
const vectorStore = new SupabaseVectorStore({ /* config */ });
const index = await VectorStoreIndex.fromDocuments(documents, { vectorStore });

// 3. Query
const queryEngine = index.asQueryEngine();
const response = await queryEngine.query('What is the return policy?');
console.log(response.toString()); // Answer with citations
```

## Pattern 2: Hybrid Search (Vector + Keyword)

**Source**: LlamaIndex + production deployments

**Why**: Pure vector search misses exact matches; pure keyword search misses semantic similarity.

```
Query → [Vector Search] + [BM25/FTS] → Reciprocal Rank Fusion → Top-K → LLM
```

**Implementation with Supabase**:
- pgvector for semantic search
- PostgreSQL full-text search for keyword matching
- RRF (Reciprocal Rank Fusion) to merge results

## Pattern 3: Chunking Strategies

| Strategy | Best For | Chunk Size |
|----------|---------|------------|
| **Fixed size** | Simple documents | 512-1024 tokens |
| **Sentence-based** | Articles, blogs | 3-5 sentences |
| **Semantic** | Technical docs | Variable (by topic) |
| **Recursive** | Structured docs | Hierarchical |
| **Document-level** | Short docs (<1 page) | Whole document |

**Golden Rule**: Chunk size should match your query granularity. If users ask specific questions, use smaller chunks (256-512). If users ask broad questions, use larger chunks (1024-2048).

## Pattern 4: Citation & Source Tracking

**Source**: LlamaIndex

**Best Practice**: Every RAG response should cite its sources.

```typescript
const response = await queryEngine.query(question);

// Access source nodes
for (const node of response.sourceNodes) {
  console.log(`Source: ${node.metadata.filename}`);
  console.log(`Score: ${node.score}`);
  console.log(`Text: ${node.text.substring(0, 100)}...`);
}
```

## Pattern 5: Evaluation (from RAGAS)

| Metric | What It Measures | Target |
|--------|-----------------|--------|
| **Faithfulness** | Is the answer supported by context? | >0.85 |
| **Relevancy** | Is the retrieved context relevant? | >0.80 |
| **Context Precision** | Are relevant docs ranked higher? | >0.75 |
| **Answer Correctness** | Is the answer factually correct? | >0.80 |

## Anti-Patterns

1. **No evaluation**: Always measure RAG quality before deploying
2. **Single embedding model**: Test multiple embedding models (OpenAI, Cohere, local)
3. **Fixed chunk size**: Different document types need different chunking strategies
4. **No reranking**: Add a reranker (Cohere, cross-encoder) after initial retrieval
5. **Ignoring metadata**: Use metadata filters (date, source, category) to improve precision
