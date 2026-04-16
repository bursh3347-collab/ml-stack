# Ray

> Unified distributed compute framework — scale any Python workload from laptop to cluster

| Metric | Data |
|--------|------|
| GitHub | https://github.com/ray-project/ray |
| Stars | 35,000+ |
| License | Apache-2.0 |
| Language | Python (API) + C++ (core) |
| Last Updated | Active daily |
| Contributors | 1,000+ |

## TEMC Scoring

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Technology | 88 | Elegant actor-based distributed computing model. Ray Core (tasks/actors) + Ray Data (streaming datasets) + Ray Train (distributed training) + Ray Serve (model serving) + Ray Tune (hyperparameter tuning). Anyscale (commercial) backed. |
| E Ecosystem | 80 | 35k Stars, 1000+ contributors, adopted by OpenAI, Uber, Spotify, Shopify. Anyscale provides managed Ray. Strong integration with PyTorch, HuggingFace, vLLM (runs on Ray). Active community and conference (Ray Summit). |
| M Market | 72 | Standard for distributed ML training and serving. But for solo devs, distributed compute is rarely needed at MVP stage. Market is enterprise/scale-focused. Growing relevance as LLM fine-tuning becomes mainstream. |
| C Combo | 68 | Powers vLLM's distributed inference. Could be used for parallel data processing pipelines. But adds significant infrastructure complexity for a solo dev. Relevant when scaling beyond single GPU. |
| **Overall** | **76** | T×0.25(22.0) + E×0.20(16.0) + M×0.30(21.6) + C×0.25(17.0) = **77** |

## Architecture Highlights

```
ray/
├── python/ray/
│   ├── _private/           ← Core runtime (GCS, Raylet, scheduling)
│   ├── data/               ← Ray Data — streaming dataset processing
│   ├── train/              ← Ray Train — distributed training
│   ├── serve/              ← Ray Serve — scalable model serving
│   ├── tune/               ← Ray Tune — hyperparameter optimization
│   └── workflow/           ← Ray Workflows — durable execution
├── src/ray/                ← C++ core (GCS server, Raylet, object store)
└── dashboard/              ← Web dashboard for cluster monitoring
```

**Key Design Decisions:**
- **Actor model**: Stateful distributed objects — intuitive abstraction for distributed computing
- **Object Store (Plasma)**: Shared memory for zero-copy data transfer between tasks
- **GCS (Global Control Store)**: Centralized metadata management with fault tolerance
- **Unified API**: Same framework for training, serving, tuning, and data processing
- **Autoscaling**: Automatic cluster scaling based on workload demand

## Best Practices Extracted

1. **Actor-based distributed pattern**: Stateful actors for distributed state management — applicable beyond ML
2. **Shared memory object store**: Zero-copy data passing between distributed components — critical for large tensor/dataset workflows
3. **Unified train→serve pipeline**: Same framework from training to production serving eliminates glue code
4. **Placement groups**: Fine-grained GPU/CPU resource allocation — pattern for multi-model serving

## Competitor Comparison

| | Ray | Dask | Spark | Celery | Kubernetes Jobs |
|---|-----|------|-------|--------|----------------|
| Focus | ML-first distributed | General parallel | Big data | Task queue | Container orchestration |
| ML Native | ✅ Deep | Partial | Partial | ❌ | ❌ |
| GPU Support | ✅ First-class | Limited | Limited | ❌ | Manual |
| Serving | Ray Serve | ❌ | ❌ | ❌ | Manual |
| Learning Curve | Moderate | Easy | Steep | Easy | Steep |
| Scale | 10,000+ nodes | 1,000+ | 10,000+ | 1,000+ | Unlimited |

## ⚠️ Why It Might NOT Be Worth It

- **Overkill for solo dev**: If you're running on a single GPU/machine, Ray adds complexity with no benefit
- **Infrastructure overhead**: Running a Ray cluster requires DevOps expertise
- **Memory hungry**: Ray's object store consumes significant RAM
- **Debugging distributed code**: When things go wrong in distributed systems, debugging is 10x harder
- **Managed cost**: Anyscale pricing is enterprise-tier

## Solo Dev Verdict

**Skip at MVP, remember for scale.** Ray is genuinely excellent infrastructure — it powers OpenAI's training and vLLM's distributed inference. But a solo dev building AI SaaS doesn't need distributed compute until reaching significant scale. **Bookmark it for Phase 2** when you need to: (1) fine-tune large models across multiple GPUs, (2) serve models with autoscaling, or (3) process massive datasets in parallel. For now, single-machine tools (Ollama, vLLM on one GPU) cover 95% of solo dev needs.
