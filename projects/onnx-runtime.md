# ONNX Runtime

> Microsoft's cross-platform ML inference accelerator — run any model, anywhere, fast

| Metric | Data |
|--------|------|
| GitHub | https://github.com/microsoft/onnxruntime |
| Stars | 15,000+ |
| License | MIT |
| Language | C++ (core) + Python/C#/Java/JS bindings |
| Last Updated | Active daily |
| Contributors | 500+ |

## TEMC Scoring

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Technology | 85 | Production-grade inference engine with hardware acceleration (CUDA, TensorRT, DirectML, CoreML, NNAPI). Graph optimization passes, quantization support (INT8/INT4), and operator fusion. Supports ONNX format as universal interchange. |
| E Ecosystem | 72 | 15k Stars, strong Microsoft backing. Used in Windows ML, Azure ML, Office 365, Bing. ONNX Model Zoo provides pre-converted models. But community is more enterprise/infra-focused than grassroots. |
| M Market | 68 | Critical infrastructure for edge/mobile ML deployment. But for LLM serving, vLLM/TGI dominate. ONNX Runtime GenAI module catching up for LLM inference. Market is niche but stable. |
| C Combo | 65 | Good for optimizing models before deployment. Convert PyTorch/TF models to ONNX, optimize, deploy. But for a solo dev using API-based LLMs, limited direct value. Relevant if self-hosting models on constrained hardware. |
| **Overall** | **72** | T×0.25(21.25) + E×0.20(14.4) + M×0.30(20.4) + C×0.25(16.25) = **72** |

## Architecture Highlights

```
onnxruntime/
├── onnxruntime/core/         ← Core inference engine (C++)
│   ├── graph/                ← ONNX graph representation & optimization
│   ├── optimizer/            ← Graph transformation passes
│   ├── providers/            ← Execution providers (CUDA, TensorRT, DirectML...)
│   └── session/              ← InferenceSession management
├── onnxruntime/python/       ← Python bindings
├── js/                       ← ONNX Runtime Web (WebAssembly + WebGL)
└── onnxruntime-genai/        ← LLM-specific inference (new)
```

**Key Design Decisions:**
- **Execution Providers**: Pluggable hardware acceleration — same model runs on CPU, GPU, NPU, mobile
- **Graph Optimization**: Multi-level optimization passes (basic → extended → layout) automatically fuse and simplify ops
- **ONNX as interchange**: Convert from any framework, optimize once, deploy anywhere
- **GenAI Module**: New component specifically for LLM inference with KV-cache, beam search, sampling

## Best Practices Extracted

1. **Model optimization pipeline**: Export → Optimize → Quantize → Deploy pattern applicable to any ML deployment
2. **Execution provider abstraction**: Hardware-agnostic inference — write once, accelerate everywhere
3. **Graph optimization passes**: Operator fusion, constant folding, shape inference — applicable patterns for any computation graph
4. **INT8/INT4 quantization**: 2-4x speedup with minimal accuracy loss — critical for edge deployment

## Competitor Comparison

| | ONNX Runtime | TensorRT | TFLite | Core ML | vLLM |
|---|-------------|----------|--------|---------|------|
| Focus | Universal inference | NVIDIA GPU max perf | Mobile/edge | Apple devices | LLM serving |
| Platform | Cross-platform | NVIDIA only | Mobile | Apple only | Server GPU |
| LLM Support | Growing (GenAI) | TensorRT-LLM | Limited | Limited | Native |
| Quantization | INT8/INT4 | INT8/FP8 | INT8/FP16 | INT8 | AWQ/GPTQ |
| Ease of Use | Moderate | Complex | Easy | Easy | Easy |

## ⚠️ Why It Might NOT Be Worth It

- **Not the best at anything specific**: TensorRT beats it on NVIDIA, CoreML beats it on Apple, vLLM beats it for LLMs
- **ONNX conversion pain**: Not all PyTorch ops convert cleanly to ONNX — edge cases cause debugging nightmares
- **For API-based LLM apps**: Zero relevance if you're calling OpenAI/Anthropic APIs
- **Complexity**: Setting up execution providers and optimization pipelines requires ML infra expertise

## Solo Dev Verdict

**Skip unless self-hosting models on diverse hardware.** For a solo dev building AI SaaS with API-based LLMs (OpenAI, Anthropic), ONNX Runtime adds no value. It becomes relevant if you need to: (1) self-host models on edge/mobile, (2) optimize inference cost by running on CPUs/NPUs, or (3) deploy models in browsers via ONNX Runtime Web. It's infrastructure-layer tooling — important at scale, irrelevant at MVP stage.
