# TensorFlow

> Google's end-to-end open-source machine learning platform.

| Metric | Data |
|--------|------|
| GitHub | [tensorflow/tensorflow](https://github.com/tensorflow/tensorflow) |
| Stars | ~190,000 |
| Forks | ~74,000 |
| License | Apache-2.0 |
| Language | Python + C++ |
| Last Update | 2026-04 (active) |
| Contributors | 3,500+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 85 | TF 2.x with Keras, TFLite for mobile/edge, TF Serving for production. Mature but complex. |
| E Ecosystem | 88 | 190k stars (most starred ML repo). Google-backed. TFHub, TFX, TFLite. But research community shifted to PyTorch. |
| M Market | 72 | Losing research market to PyTorch. Still strong in production/mobile/edge (TFLite). Google Cloud ML integration. |
| C Combo | 60 | Python-only. TensorFlow.js exists but niche. Less relevant for Tianzi's stack than PyTorch ecosystem. |
| **Overall** | **75** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 74.9 |

## Core Value
End-to-end ML platform with production focus. TFLite for mobile/edge deployment. TFX for ML pipelines. TF Serving for scalable inference. Still the standard for production ML at Google scale.

## Architecture Highlights
- **Keras Integration**: High-level API built into TF 2.x
- **TFLite**: Model optimization and deployment for mobile/edge
- **TF Serving**: Production model serving with versioning, A/B testing
- **TFX**: End-to-end ML pipeline framework
- **SavedModel Format**: Portable model serialization
- **TensorFlow.js**: ML in the browser and Node.js

## Extractable Patterns
- ML pipeline design (TFX reference)
- Model serving architecture (TF Serving)
- Edge/mobile deployment optimization (TFLite)
- SavedModel format for model portability
