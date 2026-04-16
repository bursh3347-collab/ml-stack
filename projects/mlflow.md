# MLflow

> The open-source ML lifecycle platform — track, reproduce, deploy

| Metric | Value |
|--------|-------|
| GitHub | [mlflow/mlflow](https://github.com/mlflow/mlflow) |
| Stars | ~20,000 |
| License | Apache-2.0 ✅ |
| Language | Python (+ JS/React UI) |
| Last Update | Active (daily commits) |
| Foundation | Linux Foundation (from Databricks) |

## TEMC Scores

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 85 | Well-architected REST API, tracking server, model registry. Supports every ML framework. Mature and battle-tested |
| E (Eco) | 88 | 20k stars, Linux Foundation governance, Databricks origin. Used by thousands of companies. Industry standard |
| M (Market) | 75 | MLOps is essential but enterprise-focused. Solo devs rarely need full experiment tracking |
| C (Combo) | 60 | Python-centric. REST API accessible from TS but heavy setup for solo dev. More relevant when doing model training |
| **Composite** | **76** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value

MLflow solves the "ML reproducibility crisis": track experiments, version models, package for deployment. Four core components: **Tracking** (log params/metrics), **Projects** (reproducible runs), **Models** (packaging), **Registry** (model versioning). If you train models, MLflow is essential.

## Architecture Highlights

- **Tracking Server** — REST API for logging experiments
- **Model Registry** — versioned model storage with staging/production stages
- **MLflow Models** — universal model packaging format (PyFunc)
- **Deployments** — deploy to SageMaker, Azure ML, Kubernetes, Docker
- **LLM tracking** — native support for LLM experiment tracking (2024+)
- **Tracing** — OpenTelemetry-based LLM call tracing

## Solo Dev Verdict

**🟡 REFERENCE** — Unless you're training custom models, MLflow is overkill for a solo SaaS dev. But study the tracking UI patterns if you're building any observability feature. The LLM tracing feature is increasingly relevant for AI SaaS debugging.

## Why It Might NOT Be Worth It

- Heavy infrastructure (tracking server, artifact store, DB backend)
- Overkill for API-based LLM apps (just use Langfuse instead)
- Python-centric, no TypeScript SDK
- Databricks-optimized — some features work best in their ecosystem
