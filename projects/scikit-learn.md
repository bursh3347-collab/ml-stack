# Scikit-learn

> Simple and efficient tools for predictive data analysis.

| Metric | Data |
|--------|------|
| GitHub | [scikit-learn/scikit-learn](https://github.com/scikit-learn/scikit-learn) |
| Stars | ~62,000 |
| Forks | ~25,000 |
| License | BSD-3-Clause |
| Language | Python (C/Cython core) |
| Last Update | 2026-04 (active) |
| Contributors | 3,000+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 85 | Comprehensive classical ML library. Consistent API (fit/predict/transform). Pipeline system. |
| E Ecosystem | 88 | 62k stars, 3000+ contributors. Core of Python ML stack. Textbook-standard library. |
| M Market | 70 | Classical ML still relevant for tabular data, feature engineering, preprocessing. But deep learning dominates hype. |
| C Combo | 55 | Python-only. API design patterns (fit/predict) are universally influential. Less direct relevance for AI Agent stack. |
| **Overall** | **73** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 72.6 |

## Core Value
The gold standard for classical machine learning. Consistent API across 100+ algorithms. Pipeline system for reproducible ML workflows. Essential for tabular data, feature engineering, and preprocessing.

## Architecture Highlights
- **Estimator API**: Consistent fit() / predict() / transform() interface for all algorithms
- **Pipeline System**: Chain preprocessing + feature engineering + model into reproducible pipeline
- **Cross-Validation**: Robust model evaluation with k-fold, stratified, time-series splits
- **Feature Engineering**: Imputation, encoding, scaling, selection, extraction
- **Model Selection**: Grid search, random search, Bayesian optimization for hyperparameters

## Extractable Patterns
- **⭐ Universal Code Candidate: Pipeline Pattern** → code-base/patterns/ml-pipeline/
- Estimator API design (fit/predict/transform consistency)
- Cross-validation strategies
- Feature engineering toolkit design
