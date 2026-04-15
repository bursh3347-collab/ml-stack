# 🗺️ ML Stack 技术趋势路线图

> 最近更新：2026-04-15

## 🟢 当前主流

| 方向 | 代表项目 | 状态 |
|------|---------|------|
| 本地LLM推理 | Ollama | 爆发增长 |
| 模型Hub生态 | HuggingFace Transformers | 事实标准 |
| RAG应用框架 | LlamaIndex | 快速增长 |
| LLM高性能服务 | vLLM | 生产标准 |
| 深度学习基础 | PyTorch | 稳定统治 |

## 🚀 崛起方向

- **Context Engineering**：取代Prompt Engineering成为Agent核心学科（Anthropic+Karpathy背书）
- **本地+云混合推理**：Ollama(开发) + OpenAI(生产) + vLLM(自托管) 三层架构
- **Agent Memory基础设施**：Mem0/Letta/EverMemOS等Agent记忆层爆发（Q1融资>$90M）
- **多模态模型**：视觉+语音+文本统一推理（HuggingFace支持300K+模型）
- **LoRA/QLoRA微调平民化**：HuggingFace PEFT让个人开发者也能微调大模型
- **Agentic AI安全**：LLM安全评估+Agent行为审计成为生产部署必备

## 📉 衰退方向

- **TensorFlow**：研究和新项目份额持续被PyTorch蚕食
- **经典ML独立使用**：scikit-learn作为独立工具被LLM+RAG管道替代
- **手动Prompt Engineering**：被Context Engineering和自动优化框架替代
- **单体LLM应用**：向Multi-Agent架构演进

## 🔮 6-12月预测

1. Ollama月活开发者突破500万，成为本地AI开发标配
2. LlamaIndex.TS成为TypeScript RAG应用的事实标准
3. Agent Memory从概念进入生产（5+家公司推出商业产品）
4. vLLM + Ollama形成"开发→生产"完整自托管管道
5. Context Engineering工具链生态爆发（IDE插件/SDK/评估框架）
6. EU AI Act 8月执法推动LLM安全评估工具需求

## 🏢 对一人公司的影响

- **核心技术栈**：LlamaIndex.TS + Ollama(开发) + OpenAI API(生产) + Supabase pgvector
- **商业机会**：AI知识SaaS（RAG即服务）、Agent安全审计工具、微调即服务
- **技能投资**：RAG pipeline设计 > 微调 > 模型训练（按ROI排序）
- **关键洞察**：在Layer 3-4（LLM Runtime + Product）工作，ROI最高。只有差异化需求时才下沉到Layer 1-2
- **MIT许可栈**：Ollama(MIT) + LlamaIndex(MIT) + HuggingFace(Apache) = 完全可商用

---

*由天工系统·代码猎手生成 | 2026-04-15*
