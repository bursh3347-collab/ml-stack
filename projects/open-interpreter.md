# Open Interpreter

> Let LLMs run code on your computer — a local Code Interpreter

| Metric | Value |
|--------|-------|
| GitHub | [OpenInterpreter/open-interpreter](https://github.com/OpenInterpreter/open-interpreter) |
| Stars | ~58,000 |
| License | AGPL-3.0 ⚠️ |
| Language | Python |
| Last Update | Active |
| Creator | Killian Lucas |

## TEMC Scores

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 80 | Clean Python architecture, LLM→code execution loop, multi-model support (OpenAI/Anthropic/local). Sandboxing via Docker |
| E (Eco) | 88 | 58k stars, viral growth, strong community. One of the most-starred AI agent projects |
| M (Market) | 78 | Code execution agents are the frontier. But safety/enterprise concerns limit adoption. Consumer-focused |
| C (Combo) | 60 | Python CLI tool, not directly embeddable in TS SaaS. AGPL license blocks proprietary use. Study patterns only |
| **Composite** | **76** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value

Open Interpreter gives LLMs the ability to **execute code locally** — Python, JavaScript, Shell, AppleScript. It's like ChatGPT's Code Interpreter but running on YOUR machine with full system access. The core insight: LLMs + code execution = general-purpose AI agent.

## Architecture Highlights

- **Core loop** — User message → LLM generates code → Execute → Return output → LLM continues
- **Multi-language** — Python, JavaScript, Shell, HTML, AppleScript, R
- **Multi-model** — OpenAI, Anthropic, local via Ollama/LiteLLM
- **Computer API** — mouse, keyboard, screen, clipboard control
- **Profiles** — configurable system prompts and model settings
- **Docker sandbox** — optional containerized execution

## Key Components

1. `interpreter/core/` — main loop, LLM interface, code execution
2. `interpreter/terminal_interface/` — CLI/TUI interface
3. `interpreter/computer_use/` — system interaction APIs
4. `interpreter/code_interpreters/` — language-specific executors

## Solo Dev Verdict

**🟡 STUDY PATTERN** — AGPL license means you can't use code in proprietary SaaS. But study the LLM→code execution loop architecture — it's the foundation for all AI agent systems. If you build code-execution features, this is the reference implementation.

## Why It Might NOT Be Worth It

- **AGPL-3.0** ⚠️ — Cannot use in proprietary SaaS without open-sourcing your entire app
- Security risk — LLMs executing code with system access
- Python CLI — not embeddable as library in TS projects
- Viral stars ≠ production readiness — many stars from hype, not enterprise use
- Creator's focus shifting to new projects (01 Light, etc.)
