# RAG (Retrieval-Augmented Generation) Patterns

> Best practices extracted from LlamaIndex (49k⭐) and the broader RAG ecosystem.

*Sources: run-llama/llama_index (49k⭐), multiple RAG research papers*

## 1. Basic RAG Pipeline

```
[Documents] → [Chunking] → [Embedding] → [Vector Store]
                                              |
[User Query] → [Embedding] → [Retrieval] → [Context + Query] → [LLM] → [Response]
```

**Key Decisions**:
- **Chunk size**: 512-1024 tokens (balance between context and precision)
- **Chunk overlap**: 20-50 tokens (preserve context at boundaries)
- **Embedding model**: OpenAI text-embedding-3-small (cost) or large (quality)
- **Top-K**: Retrieve 3-5 chunks (more = more noise)

## 2. Advanced RAG Patterns

### Hybrid Search (Vector + Keyword)
- Combine semantic search (embeddings) with keyword search (BM25)
- Re-rank with cross-encoder for best results
- LlamaIndex supports this natively via `QueryFusionRetriever`

### Hierarchical Indexing
- Create summary index for documents, detail index for chunks
- Query summary first, then drill into relevant chunks
- Reduces latency and improves relevance for large corpora

### Sentence Window Retrieval
- Embed individual sentences for precision
- Retrieve surrounding window (±2-3 sentences) for context
- Best for Q&A use cases

### Parent-Child Retrieval
- Embed small chunks (child) for matching precision
- Return parent chunk for richer context
- Balances precision and context

## 3. Evaluation Framework

| Metric | What It Measures | Tool |
|--------|-----------------|------|
| **Faithfulness** | Response grounded in retrieved context | RAGAS |
| **Relevancy** | Retrieved chunks relevant to query | RAGAS |
| **Context Recall** | Are all relevant docs retrieved? | RAGAS |
| **Answer Correctness** | Does answer match ground truth? | Custom |

## 4. Production RAG Checklist

- [ ] Chunking strategy tested (size, overlap, method)
- [ ] Embedding model selected and benchmarked
- [ ] Hybrid search (vector + keyword) implemented
- [ ] Re-ranking enabled for top results
- [ ] Metadata filtering available
- [ ] Evaluation pipeline set up (RAGAS or custom)
- [ ] Caching layer for repeated queries
- [ ] Source attribution in responses
- [ ] Error handling for empty retrievals
- [ ] Monitoring: latency, retrieval quality, user satisfaction

## 5. Common Anti-Patterns

| Anti-Pattern | Problem | Solution |
|-------------|---------|----------|
| Too large chunks | Noisy context dilutes answer | Use 512-1024 tokens |
| No overlap | Context lost at boundaries | Add 20-50 token overlap |
| Too many results | LLM confused by irrelevant context | Limit to top 3-5 + re-rank |
| No evaluation | Can't measure improvement | Set up RAGAS pipeline |
| Ignoring metadata | Miss filtering opportunities | Add date, source, category |
| No caching | Repeated queries hit vector DB | Cache embeddings + results |

## LlamaIndex TypeScript Quick Start

```typescript
import { VectorStoreIndex, SimpleDirectoryReader } from 'llamaindex';

// 1. Load documents
const documents = await new SimpleDirectoryReader().loadData('./data');

// 2. Create index
const index = await VectorStoreIndex.fromDocuments(documents);

// 3. Query
const queryEngine = index.asQueryEngine();
const response = await queryEngine.query('What is the main topic?');
console.log(response.toString());
```

**天子 Note**: LlamaIndex.TS is the most viable RAG framework for the TypeScript stack.
