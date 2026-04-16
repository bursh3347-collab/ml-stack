# DSPy

> Programming over prompting — the framework that replaces prompt engineering with code

| Metric | Value |
|--------|-------|
| GitHub | [stanfordnlp/dspy](https://github.com/stanfordnlp/dspy) |
| Stars | ~22,000 |
| License | MIT ✅ |
| Language | Python |
| Last Update | Active (daily commits) |
| Origin | Stanford NLP Group |

## TEMC Scores

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 88 | Paradigm shift: signatures, modules, optimizers replace prompt strings. Auto-optimization via BootstrapFewShot, MIPRO. Clean abstractions |
| E (Eco) | 82 | 22k stars, Stanford backing, growing industry adoption. Active Discord, weekly releases. Databricks partnership |
| M (Market) | 85 | Prompt optimization is THE 2026 bottleneck. DSPy solves it programmatically. Competes with LangChain but philosophically different |
| C (Combo) | 72 | Python-only, but the optimization patterns transfer to any language. Can wrap as API for Next.js consumption |
| **Composite** | **82** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value

DSPy replaces **prompt engineering** with **programming**. Instead of writing prompts, you define `Signatures` (input/output specs) and `Modules` (composable LLM programs). DSPy's optimizers automatically find the best prompts, few-shot examples, and fine-tuning data. It's like PyTorch for LLM applications.

## Architecture Highlights

- **Signatures** — declarative I/O specs: `"question -> answer"`
- **Modules** — composable building blocks: `ChainOfThought`, `ReAct`, `ProgramOfThought`
- **Optimizers** — auto-tune prompts: `BootstrapFewShot`, `MIPRO`, `BootstrapFinetune`
- **Assertions** — runtime constraints on LLM outputs
- **Multi-model** — OpenAI, Anthropic, local models via litellm

## Key Insight

> DSPy treats LLM calls like neural network layers — you define the architecture, the optimizer finds the weights (prompts/examples). This is fundamentally different from LangChain's "chains of prompt templates" approach.

## Solo Dev Verdict

**🔴 ESSENTIAL** — If you're building any LLM-powered feature, DSPy's approach (programming > prompting) will save you weeks of prompt engineering. Use it as a Python backend service behind your Next.js API routes. The optimization patterns are the real value.

## Why It Might NOT Be Worth It

- Python-only, no TypeScript version
- Learning curve — requires understanding the programming paradigm
- Optimization can be slow and expensive (many LLM calls)
- Less flexible for highly custom prompting scenarios
- Academic origin means some rough edges in production
