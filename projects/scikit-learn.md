# Scikit-learn

> Machine learning in Python — the gold standard for classical ML

| Metric | Data |
|------|------|
| GitHub | https://github.com/scikit-learn/scikit-learn |
| Stars | 65,830 |
| Forks | 26,942 |
| License | BSD-3-Clause |
| Language | Python / Cython |
| Last Updated | 2026-04-15 |
| Open Issues | 2,041 |
| Contributors | 2,000+ |
| Created | 2010-08-17 |

## TEMC Scoring

| Dimension | Score | Rationale |
|------|------|------|
| T (Tech) | 90 | Gold standard API design in ML. Consistent fit/predict/transform interface. Comprehensive: classification, regression, clustering, dimensionality reduction, preprocessing. Excellent documentation. |
| E (Ecosystem) | 85 | 65k stars, 26k forks. Used by virtually every data scientist. Foundational dependency for many ML tools. NumPy/SciPy ecosystem backbone. |
| M (Market) | 60 | Mature, established. Classical ML is being overshadowed by deep learning/LLMs in hype but remains essential for tabular data, feature engineering, and quick prototyping. Not a growth area. |
| C (Combo) | 60 | Python only. Classical ML is less relevant for LLM-era Micro SaaS products. But useful for: data preprocessing, feature engineering, classification tasks in SaaS features (spam detection, recommendation). |
| **Composite** | **73** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value
Scikit-learn is the most well-designed ML library ever built. Its consistent API (fit/predict/transform), excellent documentation, and comprehensive algorithm coverage make it the starting point for any ML task. Its API design patterns have influenced virtually every subsequent ML framework.

## Architecture Highlights
- **Estimator API**: Consistent fit()/predict()/transform() across all algorithms
- **Pipeline**: Chain preprocessing + model into a single deployable unit
- **Cross-Validation**: Built-in model evaluation with multiple strategies
- **Feature Engineering**: Scalers, encoders, imputers, polynomial features
- **Model Selection**: GridSearch, RandomSearch, Bayesian optimization

## Key Modules
1. **sklearn.pipeline** — ML pipeline construction (small, independent, highly extractable)
2. **sklearn.preprocessing** — Feature scaling and encoding (medium, independent)
3. **sklearn.model_selection** — Cross-validation and hyperparameter tuning (medium, independent)
4. **sklearn.ensemble** — Random forests, gradient boosting, bagging (medium, independent)
5. **sklearn.metrics** — Evaluation metrics (small, independent)

## Extractable Patterns
- ⭐ **通用代码候选**: Pipeline pattern (chain transformations) → code-base/data-pipeline/
- ⭐ **通用代码候选**: Estimator API design pattern → code-base/api/ml-interface/
- Feature preprocessing patterns for tabular data
- Model evaluation/metrics patterns

## Why It Might NOT Be Worth It (反证)
- LLM era has shifted focus away from classical ML
- For SaaS products, pre-built AI APIs are faster than training custom sklearn models
- Not relevant for 天子's primary focus areas (AI Agent, LLM applications)
- Tabular ML tasks are increasingly handled by AutoML tools

## 天子 Verdict
🟢 **LOW PRIORITY** — Excellent library, but not aligned with 天子's current strategy. The API design patterns (Pipeline, Estimator interface) are worth studying for software design education. Revisit if building data analysis or recommendation features for SaaS.
