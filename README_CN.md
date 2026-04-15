[English](README.md) | [中文](README_CN.md)

# 🧠 ml-stack

![Stars](https://img.shields.io/github/stars/bursh3347-collab/ml-stack?style=flat-square)
![License](https://img.shields.io/github/license/bursh3347-collab/ml-stack?style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/bursh3347-collab/ml-stack?style=flat-square)

> ⭐ 成熟度: **L1 成长期** — 7个项目已分析，最佳实践已提炼。

从全球顶尖 **7个机器学习、深度学习和LLM开源项目** 中拆解精华、提炼最佳实践、深度分析。每个项目使用 [TEMC评分体系](#temc评分) 量化评估。

## 📊 数据看板（2026-04-15）

| 指标 | 数值 |
|------|------|
| 已分析项目 | 7 |
| 覆盖总Stars | 813,000+ |
| 最佳实践文档 | 3篇 |
| TEMC评分范围 | 71-89 |

## 🏆 项目排名（按TEMC评分）

| 排名 | 项目 | Stars | TEMC | 优先级 |
|------|------|-------|------|--------|
| 1 | [HuggingFace Transformers](projects/huggingface-transformers.md) | 159k | **89** | 🔴 必备 |
| 1 | [Ollama](projects/ollama.md) | 169k | **89** | 🔴 必备 |
| 3 | [LlamaIndex](projects/llamaindex.md) | 48k | **86** | 🔴 必备 |
| 3 | [vLLM](projects/vllm.md) | 76k | **86** | 🟡 重要 |
| 5 | [PyTorch](projects/pytorch.md) | 99k | **79** | 🟡 基础 |
| 6 | [Scikit-learn](projects/scikit-learn.md) | 65k | **73** | 🟢 参考 |
| 7 | [TensorFlow](projects/tensorflow.md) | 194k | **71** | 🟢 遗产 |

## 📋 仓库内容

### 对比与最佳实践

- [📊 全面横向对比表](comparison.md) — 7个项目并排对比
- [🚀 模型服务模式](best-practices/model-serving.md) — OpenAI兼容API、连续批处理、优雅降级
- [🔍 RAG模式](best-practices/rag-patterns.md) — 管道设计、混合搜索、分块策略、评估方法
- [🎯 微调指南](best-practices/fine-tuning.md) — LoRA/QLoRA、数据集准备、何时不该微调

## 🎯 一人AI SaaS最优ML技术栈

```
第4层（产品层）：  LlamaIndex.TS + Next.js + Supabase pgvector
第3层（LLM运行时）：Ollama（开发）+ OpenAI API（生产）+ vLLM（自托管）
第2层（模型层）：  HuggingFace Transformers（微调+模型中心）
第1层（基础层）：  PyTorch（理解原理，非日常编码）
```

在 **第3-4层工作获得最大ROI**。仅当需要定制模型构建差异化时，才深入第1-2层。

## 🏗️ 仓库结构

```
ml-stack/
├── README.md              ← 英文版
├── README_CN.md           ← 你在这里
├── projects/              ← 详细项目分析（TEMC评分）
├── best-practices/        ← 跨项目提炼的模式
├── code/                  ← 可提取代码（L2阶段）
├── comparison.md          ← 全面横向对比表
└── SOURCES.md             ← 所有来源项目+License
```

## <a id="temc评分"></a>📊 TEMC评分体系

**综合评分** = T×0.25 + E×0.20 + M×0.30 + C×0.25

- **T（技术分）**: 代码质量、架构设计、技术栈匹配度、文档质量
- **E（生态分）**: Stars/Forks、社区活跃度、生态集成度、维护者信誉
- **M（时机分）**: 市场时机、竞品稀缺度、趋势匹配度、可商用性
- **C（组合分）**: 技术栈兼容性、模块可拆解性、商业组合价值、学习成本

## ⚔️ 天子点评

**Ollama + LlamaIndex是一人AI SaaS的杀手组合。** Ollama提供本地LLM推理（零API成本），LlamaIndex.TS提供完整的TypeScript RAG管道——数据加载、分块、索引、检索和生成。

**HuggingFace是你的模型超市。** 不要从头训练。浏览50万+预训练模型，必要时用LoRA微调，通过Inference API部署或下载到Ollama。

**vLLM用于大规模自托管。** 连续批处理比朴素服务提供2-4倍吞吐量。但对于起步阶段的独立开发者，OpenAI API + Ollama覆盖95%的使用场景。

**跳过TensorFlow。** PyTorch赢得了研究和创业生态。TensorFlow是遗产——除非你要部署到边缘设备用TFLite。

## License

本分析仓库使用MIT许可。各项目有自己的许可证——详见 [SOURCES.md](SOURCES.md)。
