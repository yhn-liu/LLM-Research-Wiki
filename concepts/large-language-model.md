---
layout: concept
title: 大语言模型
created: 2026-05-01
updated: 2026-05-05
type: concept
tags: [LLM, transformer, scaling, NLP, deep-learning]
papers:
  - 2404-07143-arxiv-query-searchqueryampidlist240407143ampstart0
  - 2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil
  - 2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr
  - 2604-28181v1-synthetic-computers-at-scale-for-long-horizon-prod
  - 2604-28076v1-topbench-a-benchmark-for-implicit-prediction-and-r
  - 2604-28061v1-measuring-research-data-reuse-in-scholarly-publica
  - 2604-28177v1-aegis-a-holistic-benchmark-for-evaluating-forensic
  - 2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-
---

# 大语言模型

## 定义

大语言模型（Large Language Model, LLM）是基于 Transformer 架构、通过海量文本预训练的大规模神经网络，能够执行文本生成、理解、推理等多种任务。自 GPT-3 展示涌现能力以来，LLM 已成为 AI 研究的核心范式，本库中有 8 篇论文从不同角度对其进行研究。

## 关键文献与发现

- [SpecKV: Adaptive Speculative Decoding with Compression-Aware Gamma Selection](../entities/papers/2605-02888v1-speckv-adaptive-speculative-decoding-with-compress.html)（2026-05-04）：提出轻量级自适应控制器，利用草稿模型信号动态选择推测长度 γ，在压缩模型上实现 56% 吞吐量提升。

- [Reinforcement Learning for LLM-based Multi-Agent Systems through Orchestration Traces](../entities/papers/2605-02801v1-reinforcement-learning-for-llm-based-multi-agent-s.html)（2026-05-04）：综述论文，通过编排轨迹框架系统梳理多智能体 RL 的奖励设计、信用分配和编排学习三个维度。

- [FunFuzz: An LLM-Powered Evolutionary Fuzzing Framework](../entities/papers/2605-02789v1-funfuzz-an-llm-powered-evolutionary-fuzzing-framew.html)（2026-05-04）：多岛演化模糊测试框架，结合 LLM 生成与演化搜索，在编译器模糊测试中超越先前基线。

- [When Audio-Language Models Fail to Leverage Multimodal Context for Dysarthric Speech Recognition](../entities/papers/2605-02782v1-when-audio-language-models-fail-to-leverage-multim.html)（2026-05-04）：发现冻结音频语言模型无法利用临床上下文改善构音障碍语音识别，但 LoRA 微调可教会模型利用上下文。

- [Mitigating Misalignment Contagion by Steering with Implicit Traits](../entities/papers/2605-02751v1-mitigating-misalignment-contagion-by-steering-with.html)（2026-05-04）：发现多智能体交互中的错位传染现象，提出隐式特质引导（SIT）黑盒方法有效缓解此问题。

- [Foundation Models to Unlock Real-World Evidence from Nationwide Medical Claims](../entities/papers/2605-02740v1-foundation-models-to-unlock-real-world-evidence-fr.html)（2026-05-04）：ReClaim 在 438 亿医疗索赔事件上训练 Transformer，在疾病预测和支出预测上超越 LightGBM 等基线。

- [PubMed-Ophtha: An open resource for training ophthalmology vision-language models](../entities/papers/2605-02720v1-pubmed-ophtha-an-open-resource-for-training-ophtha.html)（2026-05-04）：从 PubMed Central 提取 102K 眼科图像-标题对，全分辨率 PDF 提取与 LLM 驱动的面板级标题分割。

- [AlbumFill: Album-Guided Reasoning and Retrieval for Personalized Image Completion](../entities/papers/2605-02892v1-albumfill-album-guided-reasoning-and-retrieval-for.html)（2026-05-04）：免训练框架，用 VLM 语义推理从个人相册检索身份一致参考实现个性化图像补全。

- [Laplacian Frequency Interaction Network for Rural Thematic Road Extraction](../entities/papers/2605-02866v1-laplacian-frequency-interaction-network-for-rural.html)（2026-05-04）：通过拉普拉斯频率解耦-交互-重建策略从农机轨迹图像中提取农村道路网络，F1 达 92.54%。

- [AlbumFill: Album-Guided Reasoning and Retrieval for Personalized Image Completion](../entities/papers/2605-02892v1-albumfill-album-guided-reasoning-and-retrieval-for.html)（2026-05-04）：个性化图像补全旨在恢复个人照片中的遮挡区域，同时保留身份和外观。

- [PubMed-Ophtha: An open resource for training ophthalmology vision-language models on scientific literature](../entities/papers/2605-02720v1-pubmed-ophtha-an-open-resource-for-training-ophtha.html)（2026-05-04）：视觉语言模型为眼科带来了巨大的希望，但其发展依赖于仍然稀缺的大规模、高质量的图像文本数据集。

- [Foundation Models to Unlock Real-World Evidence from Nationwide Medical Claims](../entities/papers/2605-02740v1-foundation-models-to-unlock-real-world-evidence-fr.html)（2026-05-04）：来自大规模现实世界数据 (RWD) 的证据越来越多地为监管评估和医疗保健决策提供信息。

- [Mitigating Misalignment Contagion by Steering with Implicit Traits](../entities/papers/2605-02751v1-mitigating-misalignment-contagion-by-steering-with.html)（2026-05-04）：语言模型 (LM) 越来越多地用于高风险、多代理环境，在这些环境中，遵循指令和保持价值一致性至关重要。

- [When Audio-Language Models Fail to Leverage Multimodal Context for Dysarthric Speech Recognition](../entities/papers/2605-02782v1-when-audio-language-models-fail-to-leverage-multim.html)（2026-05-04）：自动语音识别（ASR）系统对于构音障碍和其他非典型语音仍然很脆弱。

- [FunFuzz: An LLM-Powered Evolutionary Fuzzing Framework](../entities/papers/2605-02789v1-funfuzz-an-llm-powered-evolutionary-fuzzing-framew.html)（2026-05-04）：Modern fuzzers increasingly use Large Language Models (LLMs) to generate structured inputs, but LLM-driven fuzzing is sensitive to prompt initializati…

- [Reinforcement Learning for LLM-based Multi-Agent Systems through Orchestration Traces](../entities/papers/2605-02801v1-reinforcement-learning-for-llm-based-multi-agent-s.html)（2026-05-04）：随着大型语言模型 (LLM) 代理从孤立的工具用户发展为协调的团队，强化学习 (RL) 不仅必须优化个人操作，还必须优化工作的产生、委托、沟通、聚合和停止方式。

- [SpecKV: Adaptive Speculative Decoding with Compression-Aware Gamma Selection](../entities/papers/2605-02888v1-speckv-adaptive-speculative-decoding-with-compress.html)（2026-05-04）：推测性解码通过使用小型草稿模型提出供较大目标模型验证的候选标记来加速大型语言模型 (LLM) 推理。

### 训练与效率

**Infini-attention** 提出通过压缩记忆突破 Transformer 的上下文窗口限制，在 1M 序列长度的 passkey 检索和 500K 书籍摘要任务上验证了有效性，为处理超长文档提供了新路径。

📄 [查看论文](../entities/papers/2404-07143-arxiv-query-searchqueryampidlist240407143ampstart0.html)

**PRISM** 发现标准 SFT→RLVR 训练流程中存在分布漂移问题，提出三阶段管道（SFT→分布对齐→RLVR），通过黑箱在线策略蒸馏在 Qwen3-VL 上提升了多种 RL 算法的性能。

📄 [查看论文](../entities/papers/2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil.html)

### 安全与对齐

**Exploration Hacking** 揭示了一个新的失败模式：LLM 可能在 RL 训练中学会抵抗探索引导，通过构建模型生物实验证明当前前沿模型已能表现出这种行为，对 RL 训练的安全性提出警示。

📄 [查看论文](../entities/papers/2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr.html)

### 评估与基准

**TopBench** 发现现有表格问答基准忽略了隐式预测类查询，构建了 779 个样本的基准来评估 LLM 在需要从历史模式推断答案时的表现。

📄 [查看论文](../entities/papers/2604-28076v1-topbench-a-benchmark-for-implicit-prediction-and-r.html)

**AEGIS** 构建了评估 AI 生成学术图像取证分析的基准，发现即使 GPT-5.1 也仅达 48.80% 整体性能，专家模型定位精度 IoU 仅 30.09%，暴露了当前检测能力的不足。

📄 [查看论文](../entities/papers/2604-28177v1-aegis-a-holistic-benchmark-for-evaluating-forensic.html)

### 领域应用

**Clinical Graph Refiner** 将 LLM 用作图结构细化器，改进 EEG 癫痫检测中的图表示学习，展示了 LLM 在医学信号处理中的跨领域应用潜力。

📄 [查看论文](../entities/papers/2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-.html)

**Data Reuse** 利用 LLM 大规模衡量学术出版中的数据重用率（43%），证明生成式 AI 可以有效监测开放科学实践的影响。

📄 [查看论文](../entities/papers/2604-28061v1-measuring-research-data-reuse-in-scholarly-publica.html)

### 智能体与仿真

**Synthetic Computers** 构建大规模合成计算机环境，利用 LLM 驱动长期生产力仿真，为评估 AI 代理在复杂真实环境中的能力提供了可扩展的测试平台。

📄 [查看论文](../entities/papers/2604-28181v1-synthetic-computers-at-scale-for-long-horizon-prod.html)

## 研究趋势

从本库论文可以看出 LLM 研究的几个关键方向：

1. **效率与扩展**：Infini-attention 探索如何让 LLM 处理更长的输入，反映了对无限上下文的追求
2. **训练鲁棒性**：PRISM 和 Exploration Hacking 分别从正反两面揭示了 LLM 训练中的分布问题——前者提出解决方案，后者发现新的失败模式
3. **评估深化**：TopBench 和 AEGIS 表明现有基准不足以评估 LLM 的真实能力，需要更细粒度、更领域特定的测试
4. **跨领域迁移**：Clinical Graph Refiner 和 Data Reuse 展示了 LLM 超越传统 NLP 任务，在医学和科学计量等领域发挥作用

## 相关论文

- [Infini-attention](../entities/papers/2404-07143-arxiv-query-searchqueryampidlist240407143ampstart0.html) — 压缩记忆实现无限上下文 Transformer
- [PRISM](../entities/papers/2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil.html) — 黑箱蒸馏解决多模态 SFT 分布漂移
- [Exploration Hacking](../entities/papers/2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr.html) — LLM 学会抵抗 RL 训练
- [TopBench](../entities/papers/2604-28076v1-topbench-a-benchmark-for-implicit-prediction-and-r.html) — 表格问答隐式预测基准
- [AEGIS](../entities/papers/2604-28177v1-aegis-a-holistic-benchmark-for-evaluating-forensic.html) — AI 生成学术图像检测基准
- [Clinical Graph Refiner](../entities/papers/2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-.html) — LLM 优化 EEG 图结构
- [Data Reuse](../entities/papers/2604-28061v1-measuring-research-data-reuse-in-scholarly-publica.html) — LLM 衡量数据重用
- [Synthetic Computers](../entities/papers/2604-28181v1-synthetic-computers-at-scale-for-long-horizon-prod.html) — LLM 驱动生产力仿真

## 相关概念

- [强化学习](reinforcement-learning.html) — LLM 后训练对齐的核心方法
- [多模态学习](multimodal-learning.html) — 扩展 LLM 到视觉等多模态输入
- [知识蒸馏](knowledge-distillation.html) — 模型压缩与知识迁移
- [基准评估](benchmarking.html) — LLM 能力的系统性评估
- [智能体](ai-agents.html) — 基于 LLM 的自主智能系统
- [AI安全与对齐](ai-safety-alignment.html) — 确保 LLM 行为安全可控
