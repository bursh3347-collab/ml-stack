# Scikit-learn

> The gold standard for classical machine learning — clean API, battle-tested algorithms, 16 years of stability.

| Metric | Data |
|--------|------|
| GitHub | https://github.com/scikit-learn/scikit-learn |
| Stars | 65,830 |
| Forks | 26,943 |
| License | BSD-3-Clause |
| Language | Python / Cython |
| Last Commit | 2026-04-15 (today) |
| Open Issues | 2,045 |
| Created | 2010-08-17 (16 years!) |

## TEMC Scoring

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 88 | Gold standard API design (fit/predict/transform). Battle-tested algorithms. Excellent documentation. Cython optimized. Preparing v1.9 with cleanup. |
| E (Ecosystem) | 85 | 65k stars, 26k forks, 2000+ contributors. NumFOCUS sponsored. Probabl.ai commercial support. Stable, mature community. |
| M (Market) | 60 | Mature, no growth trend. Classical ML less hyped than deep learning. But evergreen — tabular data, preprocessing, model selection still essential. |
| C (Combo) | 65 | Python only. Classical ML less relevant to天子's AI Agent focus. But: preprocessing pipelines, model evaluation patterns are universal. Learning cost: low. |
| **Composite** | **73** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Analysis

```
sklearn/
├── sklearn/
│   ├── ensemble/        # Random Forest, Gradient Boosting, etc.
│   ├── linear_model/    # Linear/Logistic Regression, Lasso, etc.
│   ├── cluster/         # KMeans, DBSCAN, etc.
│   ├── preprocessing/   # Scalers, encoders, transformers
│   ├── pipeline/        # Pipeline and ColumnTransformer
│   ├── model_selection/ # Cross-validation, grid search
│   ├── metrics/         # Evaluation metrics
│   └── feature_extraction/  # Text/image feature extraction
└── doc/                 # Sphinx documentation
```

**Architecture Pattern**: Estimator pattern (fit/predict/transform), Pipeline composition, mixin-based design.

**Key Design Principle**: Consistent API — every algorithm follows the same interface.

## Core Modules

1. **Pipeline** — Chain preprocessing + model into single object (medium, low coupling)
2. **Preprocessing** — Scalers, encoders, imputers (medium, low coupling)
3. **Model Selection** — Cross-validation, hyperparameter search (medium, low coupling)
4. **Metrics** — Comprehensive evaluation metrics (small, low coupling)
5. **Ensemble Methods** — Random Forest, Gradient Boosting (medium, medium coupling)

## Extractable Components

| Module | Difficulty | Est. Time | Target |
|--------|-----------|-----------|--------|
| Pipeline/Estimator pattern | Documentation | 2h | best-practices/ |
| Preprocessing patterns | Documentation | 2h | best-practices/ |
| Model evaluation recipes | Documentation | 2h | best-practices/ |
| API design principles | Documentation | 1h | best-practices/ |

⭐ **Universal Code Candidate**: Estimator API design pattern (fit/predict/transform is universally applicable).

## Business Value

- **Pain Point**: Data preprocessing and classical ML (重要级)
- **TAM**: Part of broader $47B AI/ML market
- **Monetization**: Free. Probabl.ai offers commercial support.
- **For天子**: Essential for data preprocessing in any ML pipeline. Not directly monetizable.

## Why It Might NOT Be Worth Deep Investment

- 🔴 Classical ML less relevant to AI Agent/LLM focus
- 🔴 Python only, no TypeScript relevance
- 🔴 Mature — no differentiation opportunity
- 🟡 Slow release cycle (deliberate stability)
- ✅ But API design is the gold standard — worth studying
- ✅ Essential for tabular data tasks (still 80% of enterprise ML)
