# RAG Architecture Patterns

> Patterns extracted from LlamaIndex, LangChain, and production RAG systems.

## Pattern 1: Basic RAG Pipeline

```
Documents → Chunk → Embed → Store (Vector DB)
                                    ↓
Query → Embed → Retrieve → Rerank → Generate (LLM) → Response
```

## Pattern 2: Chunking Strategies

| Strategy | When to Use | Chunk Size |
|----------|------------|------------|
| Fixed size | Simple documents | 512-1024 tokens |
| Recursive | Structured text (markdown, code) | 256-512 tokens |
| Semantic | Dense content (papers, docs) | Variable |
| Sentence | Conversational text | 3-5 sentences |
| Document | Short documents (emails, tickets) | Full document |

**Best practice**: Overlap chunks by 10-20% to preserve context at boundaries.

```typescript
function recursiveChunk(text: string, maxSize: number, overlap: number): string[] {
  const separators = ['\n\n', '\n', '. ', ' '];
  // Try each separator, split, then recursively chunk if still too large
}
```

## Pattern 3: Hybrid Retrieval (Vector + Keyword)

```
Query → Vector Search (semantic similarity)
      → Keyword Search (BM25 exact match)
      → Reciprocal Rank Fusion (combine results)
      → Reranker (cross-encoder scoring)
      → Top-K documents → LLM
```

**Why hybrid**: Vector search catches semantic meaning, keyword search catches exact terms. Combining both beats either alone by 10-20%.

## Pattern 4: Advanced RAG Techniques

### 4a. Query Transformation
```
User query → LLM rewrites → Multiple sub-queries → Retrieve for each → Merge results
```

### 4b. Self-RAG (Retrieval-Augmented Self-Reflection)
```
Retrieve → Generate → Self-check (is answer grounded in sources?) → Retry if not
```

### 4c. Knowledge Graph RAG
```
Documents → Extract entities/relations → Build knowledge graph
Query → Graph traversal → Subgraph retrieval → LLM with graph context
```

## Pattern 5: Evaluation Metrics

| Metric | What it measures | How to compute |
|--------|-----------------|----------------|
| **Faithfulness** | Is the answer grounded in retrieved docs? | LLM judge |
| **Answer Relevancy** | Does the answer address the question? | LLM judge |
| **Context Precision** | Are retrieved docs relevant? | LLM judge |
| **Context Recall** | Did we retrieve all relevant docs? | Compare to ground truth |

## Pattern 6: Production RAG Architecture

```typescript
class RAGPipeline {
  async query(question: string): Promise<RAGResponse> {
    // 1. Query transformation
    const enhancedQuery = await this.transformQuery(question);
    
    // 2. Hybrid retrieval
    const vectorResults = await this.vectorStore.search(enhancedQuery, { topK: 10 });
    const keywordResults = await this.bm25.search(enhancedQuery, { topK: 10 });
    const merged = this.reciprocalRankFusion(vectorResults, keywordResults);
    
    // 3. Reranking
    const reranked = await this.reranker.rerank(enhancedQuery, merged, { topK: 5 });
    
    // 4. Generation with sources
    const response = await this.llm.generate({
      system: 'Answer based on the provided context. Cite sources.',
      context: reranked.map(r => r.text).join('\n\n'),
      question: enhancedQuery,
    });
    
    return { answer: response, sources: reranked };
  }
}
```

## Anti-Patterns

1. **No chunking strategy** — Dumping entire documents into vector DB
2. **No reranking** — Vector search alone has mediocre precision
3. **No evaluation** — Can't improve what you can't measure
4. **Ignoring metadata** — Chunk metadata (source, date, section) improves retrieval
5. **One-size-fits-all embeddings** — Different content types need different embedding models
