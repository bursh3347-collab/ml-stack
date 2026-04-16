# Langfuse

> LLM observability platform — traces, evals, prompt management for AI apps

| Metric | Value |
|--------|-------|
| GitHub | [langfuse/langfuse](https://github.com/langfuse/langfuse) |
| Stars | ~8,000 |
| License | MIT (core) / EE ✅ |
| Language | TypeScript (Next.js monorepo) |
| Last Update | Active (daily commits) |
| Company | Langfuse GmbH (YC W23, Berlin) |

## TEMC Scores

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 88 | Next.js + tRPC + Prisma + ClickHouse. Excellent TS monorepo architecture. Self-hostable via Docker. OpenTelemetry compatible |
| E (Eco) | 78 | 8k stars, fast growing. YC-backed, active community. Integrations with LangChain, LlamaIndex, OpenAI, Vercel AI SDK |
| M (Market) | 88 | LLM observability is THE 2026 critical need. Every AI app needs traces, evals, cost tracking. Market is exploding |
| C (Combo) | 90 | **Perfect stack match**: TypeScript, Next.js, Prisma, self-hostable. Can study architecture directly for天子's own projects |
| **Composite** | **87** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value

Langfuse is what you use **after** deploying an LLM app: trace every LLM call, measure quality, track costs, manage prompts, run evaluations. It's the "Datadog for LLMs" — but open-source and self-hostable. And it's built on YOUR exact tech stack (Next.js + TS).

## Architecture Highlights

- **Next.js monorepo** — `web/` (dashboard) + `worker/` (async processing) + `packages/`
- **tRPC** — type-safe API between frontend and backend
- **Prisma** — PostgreSQL ORM
- **ClickHouse** — analytics/traces storage (high-volume)
- **OpenTelemetry** — standard traces/spans model
- **Prompt Management** — version and deploy prompts from UI
- **Evaluations** — LLM-as-judge, human labeling, custom metrics

## Key Integrations

- OpenAI SDK (auto-instrument)
- Vercel AI SDK
- LangChain / LlamaIndex
- LiteLLM
- Python + JS/TS SDKs

## Solo Dev Verdict

**🔴 ESSENTIAL + STUDY TARGET** — Two reasons: (1) Use Langfuse to monitor your own AI SaaS products. (2) Study the codebase as a **masterclass in TypeScript SaaS architecture** — it's built on your exact stack. The monorepo structure, tRPC patterns, ClickHouse integration are all directly reusable.

## Why It Might NOT Be Worth It

- Self-hosting requires ClickHouse (heavier than just Postgres)
- EE features behind paywall (SSO, RBAC)
- Competing with well-funded players (Arize, Weights & Biases, Datadog)
- Fast-moving codebase — breaking changes possible
