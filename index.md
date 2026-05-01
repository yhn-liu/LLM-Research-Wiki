---
layout: default
title: LLM Research Wiki
---

# 🔬 LLM Research Wiki

> AI/ML 领域的维基式知识库。按概念组织，论文为据，持续更新。
> 最后更新：2026-05-01 | 概念：10 | 论文：11

---

## 🧭 知识导航

### 核心概念

| 概念 | 说明 | 论文数 |
|------|------|--------|
| [大语言模型](concepts/large-language-model.md) | GPT、LLaMA 等大规模预训练语言模型 | 8 |
| [强化学习](concepts/reinforcement-learning.md) | RLHF、RLVR、DPO、GRPO 等对齐技术 | 2 |
| [多模态学习](concepts/multimodal-learning.md) | 视觉-语言模型、跨模态推理 | 2 |
| [知识蒸馏](concepts/knowledge-distillation.md) | 教师-学生框架、黑箱蒸馏、策略蒸馏 | 1 |
| [世界模型](concepts/world-models.md) | 环境动态预测与生成 | 1 |
| [基准评估](concepts/benchmarking.md) | 标准化测试与评估方法论 | 2 |
| [智能体](concepts/ai-agents.md) | LLM 驱动的自主代理与工具使用 | 2 |
| [图神经网络](concepts/graph-neural-networks.md) | 图结构学习与推理 | 1 |
| [自动驾驶](concepts/autonomous-driving.md) | 感知、预测、规划与世界模型 | 1 |
| [AI安全与对齐](concepts/ai-safety-alignment.md) | 对齐问题、对抗训练、安全评估 | 2 |

### 技术方向

- **训练方法** → [强化学习](concepts/reinforcement-learning.md) | [知识蒸馏](concepts/knowledge-distillation.md)
- **模型架构** → [大语言模型](concepts/large-language-model.md) | [图神经网络](concepts/graph-neural-networks.md) | [世界模型](concepts/world-models.md)
- **应用场景** → [自动驾驶](concepts/autonomous-driving.md) | [医学AI](concepts/graph-neural-networks.md) | [智能体](concepts/ai-agents.md)
- **评估与安全** → [基准评估](concepts/benchmarking.md) | [AI安全与对齐](concepts/ai-safety-alignment.md)

---

## 📄 最新论文

<!-- 按日期倒序排列 -->

### 训练与对齐

- [**PRISM: Pre-alignment via Black-box On-policy Distillation**](entities/papers/2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil.md) — 三阶段训练管道：SFT→分布对齐→RLVR，解决多模态推理中的分布漂移问题
- [**Exploration Hacking: Can LLMs Learn to Resist RL Training?**](entities/papers/2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr.md) — 揭示 LLM 在 RL 训练中可能学会抵抗探索引导的新失败模式

### 世界模型与 3D 理解

- [**HERMES++: Toward a Unified Driving World Model**](entities/papers/2604-28196v1-hermes-toward-a-unified-driving-world-model-for-3d.md) — 统一 3D 场景理解与未来几何预测的驾驶世界模型

### 基准评估

- [**AEGIS: A Holistic Benchmark for AI-Generated Academic Image Forensics**](entities/papers/2604-28177v1-aegis-a-holistic-benchmark-for-evaluating-forensic.md) — 评估 AI 生成学术图像的取证分析基准
- [**TopBench: Implicit Prediction and Reasoning over Tabular QA**](entities/papers/2604-28076v1-topbench-a-benchmark-for-implicit-prediction-and-r.md) — 表格问答中的隐式预测与推理基准

### 医学 AI

- [**LLM as Clinical Graph Structure Refiner**](entities/papers/2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-.md) — 用 LLM 作为图结构细化器改进 EEG 癫痫检测

### NLP 理论

- [**On the Proper Treatment of Units in Surprisal Theory**](entities/papers/2604-28147v1-on-the-proper-treatment-of-units-in-surprisal-theo.md) — 惊讶理论中语言单位处理的统一框架

### 长上下文

- [**Leave No Context Behind: Infini-attention**](entities/papers/2404-07143-arxiv-query-searchqueryampidlist240407143ampstart0.md) — 通过压缩记忆实现无限上下文 Transformer

### 智能体与仿真

- [**Synthetic Computers at Scale**](entities/papers/2604-28181v1-synthetic-computers-at-scale-for-long-horizon-prod.md) — 大规模合成计算机环境用于长期生产力仿真

### 其他

- [**Measuring Research Data Reuse with LLM**](entities/papers/2604-28061v1-measuring-research-data-reuse-in-scholarly-publica.md) — 用 LLM 衡量学术出版中的数据重用
- [**Mapping Classroom Interaction Research**](entities/papers/2604-28098v1-mapping-the-methodological-space-of-classroom-inte.md) — AI 时代课堂互动研究的方法论空间

---

## 📊 论文索引

> 按 arXiv ID 排列的完整论文列表

| 论文 | 分类 | 日期 |
|------|------|------|
| [Infini-attention](entities/papers/2404-07143-arxiv-query-searchqueryampidlist240407143ampstart0.md) | cs.CL, cs.AI, cs.LG | 2024-04 |
| [Data Reuse with LLM](entities/papers/2604-28061v1-measuring-research-data-reuse-in-scholarly-publica.md) | cs.DL, cs.CL | 2026-04 |
| [TopBench](entities/papers/2604-28076v1-topbench-a-benchmark-for-implicit-prediction-and-r.md) | cs.CL, cs.AI, cs.LG | 2026-04 |
| [Classroom Interaction](entities/papers/2604-28098v1-mapping-the-methodological-space-of-classroom-inte.md) | cs.AI, cs.CL, cs.CY | 2026-04 |
| [PRISM](entities/papers/2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil.md) | cs.CV, cs.AI, cs.CL | 2026-04 |
| [Surprisal Theory](entities/papers/2604-28147v1-on-the-proper-treatment-of-units-in-surprisal-theo.md) | cs.CL | 2026-04 |
| [AEGIS](entities/papers/2604-28177v1-aegis-a-holistic-benchmark-for-evaluating-forensic.md) | cs.CV, cs.CY | 2026-04 |
| [Clinical Graph Refiner](entities/papers/2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-.md) | cs.AI | 2026-04 |
| [Synthetic Computers](entities/papers/2604-28181v1-synthetic-computers-at-scale-for-long-horizon-prod.md) | cs.AI, cs.CL, cs.LG | 2026-04 |
| [Exploration Hacking](entities/papers/2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr.md) | cs.LG, cs.CL | 2026-04 |
| [HERMES++](entities/papers/2604-28196v1-hermes-toward-a-unified-driving-world-model-for-3d.md) | cs.CV | 2026-04 |

---

## 🔍 搜索

> 使用浏览器的 Ctrl+F 搜索概念和论文，或浏览上方的分类导航。
