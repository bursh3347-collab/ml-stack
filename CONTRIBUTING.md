# 🤝 Contributing to ml-stack

Thank you for your interest in contributing! This repository is part of the **GitHub Open Source Knowledge Restructuring Project**.

## 📋 How to Contribute

### 1. Add a New Project Analysis

- Create `projects/[project-name].md` using the TEMC scoring template
- Include: basic metrics, TEMC scores with data backing, architecture analysis, extractable patterns, commercial value, counter-arguments
- End with `## 天子点评` — one-sentence verdict from the perspective of a one-person AI-native company

### 2. Update Existing Analyses

- Fix inaccurate data (Stars count, license, last update, etc.)
- Add new insights or counter-arguments
- Update TEMC scores with new evidence

### 3. Extract Best Practices

- Add patterns to `best-practices/` directory
- Must reference specific source projects
- Include code examples where applicable

### 4. Extract Universal Code

- Add reusable code to `code/` directory or suggest for [code-base](https://github.com/bursh3347-collab/code-base)
- Must include: source attribution, license, usage instructions, why it's good

## ✅ Quality Standards

| Requirement | Description |
|-------------|-------------|
| TEMC Scores | Must be backed by specific data points, not opinions |
| Counter-argument | Every project rated ≥80 MUST include "Why it might NOT be worth it" |
| Stars threshold | Projects must have ≥500 Stars |
| Activity | Must have commits within the last 90 days |
| License | Permissive preferred (MIT/Apache/BSD). AGPL projects must be marked ⚠️ |
| 天子点评 | One-sentence verdict required at the end of every project analysis |

## 🔄 PR Process

1. Fork this repository
2. Create your branch: `git checkout -b add/[project-name]`
3. Make your changes
4. Update `comparison.md` and `SOURCES.md` if adding a new project
5. Submit a Pull Request with a clear description

## 📐 TEMC Scoring Guide

- **T (Tech)** 0-100: Code quality(30%) + Architecture(30%) + Stack match(20%) + Docs(20%)
- **E (Ecosystem)** 0-100: Stars/Forks(30%) + Community(30%) + Integrations(20%) + Maintainer(20%)
- **M (Market)** 0-100: Timing(35%) + Competition(25%) + Trend(20%) + Commercializability(20%)
- **C (Combo)** 0-100: Stack compat(30%) + Modularity(25%) + Business combo(25%) + Learning cost(20%)
- **Composite** = T×0.25 + E×0.20 + M×0.30 + C×0.25

---

*Powered by [TEMC scoring methodology](https://github.com/bursh3347-collab) — the GitHub Open Source Knowledge Restructuring Project.*
