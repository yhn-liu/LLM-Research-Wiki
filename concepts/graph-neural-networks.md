---
layout: concept
title: 图神经网络
created: 2026-05-01
updated: 2026-05-05
type: concept
tags: [GNN, graph, neural-network, biomedical, representation-learning, message-passing]
papers:
  - 2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-
---

# 图神经网络

## 概述

图神经网络（Graph Neural Network, GNN）是一类专门处理图结构数据的深度学习模型。与传统的网格数据不同，图数据由节点和边组成，能够自然地表示实体间的关系和交互。GNN 通过消息传递（message passing）机制让每个节点聚合邻居信息来更新自身表示。近年来，LLM 与 GNN 的融合正在开辟新的研究方向。

## 文献脉络

### LLM 驱动的图结构优化

[LLM as Clinical Graph Structure Refiner: Enhancing Representation Learning in EEG Seizure Diagnosis](../entities/papers/2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-.html)（Li et al., 2026）首次将 LLM 用作图结构细化器，探索了 LLM 在图学习中的新角色。该工作针对 EEG 信号的噪声问题——现有图构建方法（无论基于相关性还是学习）都会生成冗余或不相关的边，严重影响图表示质量和下游任务性能。

研究者提出了两阶段框架：（1）使用 Transformer 边缘预测器和 MLP 构建初始图，为每个潜在边分配概率分数；（2）LLM 作为边缘集细化器，综合节点对的文本特征和统计特征做出边缘存在性判断。在 TUSZ 数据集上的实验表明，LLM 细化后的图结构更清晰、更具可解释性，且癫痫检测准确性显著提升。这项工作的核心创新在于：LLM 能够综合理解 EEG 通道间的语义关系和统计模式，做出超越纯数值相关性的边缘判断。

### GNN 的经典发展

GNN 的发展经历了从谱域到空间域的演进。2005 年 Gori 等人提出递归图神经网络（RecGNN），2009 年 Scarselli 等人系统定义了 GNN 理论框架。2014 年 Bruna 等人提出谱图卷积神经网络，2017 年 Kipf & Welling 提出简化的 GCN 成为最广泛使用的架构。2018 年 GraphSAGE 和 GAT 分别引入了采样归纳学习和注意力机制，2019 年 MPNN 统一了多种 GNN 架构。2021 年后，图 Transformer 将 Transformer 架构引入图数据处理。

## 核心主题

### LLM 与 GNN 的融合

Clinical Graph Refiner 展示了一种新的融合范式：LLM 不直接处理图数据，而是作为图结构的优化器。这种"LLM 增强图构建"的方式利用了 LLM 的推理和上下文理解能力，弥补了纯数值方法在语义理解上的不足。

### 图构建质量的重要性

该工作揭示了一个被忽视的问题：图构建质量对下游任务的影响可能超过 GNN 架构本身。冗余边和噪声边会显著降低表示学习效果，而 LLM 的介入能够有效筛选出有意义的结构关系。

### 可解释性提升

LLM 细化后的图结构更清晰、更具可解释性，这对生物医学等需要临床理解的应用场景尤为重要。可解释的图结构有助于医生理解模型的诊断依据。

### 图表示学习的演进

从节点嵌入、图嵌入到边预测和子图提取，图表示学习方法不断丰富。显式图（分子结构）、隐式图（从非图数据学习）、动态图和异构图等不同的图构建方式扩展了 GNN 的应用范围。

## 开放问题与未来方向

1. **过平滑问题**：深层 GNN 中节点表示趋于一致，失去区分性
2. **可扩展性**：处理超大规模图时的计算和内存瓶颈
3. **动态图建模**：如何有效处理图结构的动态变化
4. **LLM-GNN 深度融合**：如何更有效地结合 LLM 的推理能力和 GNN 的结构化表示
5. **异构图学习**：多种节点和边类型带来的复杂性
6. **可解释性**：GNN 决策过程的可解释性仍然是开放挑战

## 相关概念

- [大语言模型](large-language-model.html) — 与 GNN 结合增强图结构数据的理解
- [多模态学习](multimodal-learning.html) — 图数据与其他模态的融合
- [基准评估](benchmarking.html) — GNN 模型的评估方法
- [知识蒸馏](knowledge-distillation.html) — GNN 模型的压缩与迁移

## 本库相关论文

- [PubMed-Ophtha: An open resource for training ophthalmology vision-language models on scientific literature](../entities/papers/2605-02720v1-pubmed-ophtha-an-open-resource-for-training-ophtha.html)（2026-05-04）：视觉语言模型为眼科带来了巨大的希望，但其发展依赖于仍然稀缺的大规模、高质量的图像文本数据集。

- [Reinforcement Learning for LLM-based Multi-Agent Systems through Orchestration Traces](../entities/papers/2605-02801v1-reinforcement-learning-for-llm-based-multi-agent-s.html)（2026-05-04）：随着大型语言模型 (LLM) 代理从孤立的工具用户发展为协调的团队，强化学习 (RL) 不仅必须优化个人操作，还必须优化工作的产生、委托、沟通、聚合和停止方式。
