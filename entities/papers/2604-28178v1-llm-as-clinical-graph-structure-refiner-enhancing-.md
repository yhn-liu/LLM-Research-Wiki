---
layout: paper
title: "LLM as Clinical Graph Structure Refiner: Enhancing Representation Learning in EEG Seizure Diagnosis"
created: 2026-05-01
updated: 2026-05-01
type: paper
arxiv_id: 2604.28178v1
authors: "Lincan Li, Zheng Chen, Yushun Dong"
published: 2026-04-30
categories: cs.AI
tags: [ai]
source_url: https://arxiv.org/abs/2604.28178v1
pdf_url: https://arxiv.org/pdf/2604.28178v1
confidence: high
status: analyzed
---

# LLM as Clinical Graph Structure Refiner: Enhancing Representation Learning in EEG Seizure Diagnosis

## 基本信息

- **arXiv ID:** [2604.28178v1](https://arxiv.org/abs/2604.28178v1)
- **作者:** Lincan Li, Zheng Chen, Yushun Dong
- **发布日期:** 2026-04-30
- **分类:** cs.AI

## 摘要

### English

Electroencephalogram (EEG) signals are vital for automated seizure detection, but their inherent noise makes robust representation learning challenging. Existing graph construction methods, whether correlation-based or learning-based, often generate redundant or irrelevant edges due to the noisy nature of EEG data. This significantly impairs the quality of graph representation and limits downstream task performance. Motivated by the remarkable reasoning and contextual understanding capabilities of large language models (LLMs), we explore the idea of using LLMs as graph edge refiners. Specifically, we propose a two-stage framework: we first validate that LLM-based edge refinement can effectively identify and remove redundant connections, significantly improving seizure detection accuracy and producing more meaningful graph structures. Building on this insight, we develop a robust solution where an initial graph is constructed using a Transformer-based edge predictor and a multilayer perceptron, assigning probability scores to potential edges and applying a threshold to determine their existence. The LLM then acts as an edge set refiner, making informed decisions based on the textual and statistical features of node pairs to validate remaining connections. Extensive experiments on the TUSZ dataset demonstrate that our LLM-refined graph learning framework not only improves task performance but also produces clearer and more interpretable graph representations.

### 中文

脑电图 (EEG) 信号对于自动癫痫检测至关重要，但其固有的噪声使得稳健的表示学习具有挑战性。现有的图构建方法，无论是基于相关性的还是基于学习的，由于脑电图数据的噪声性质，通常会生成冗余或不相关的边缘。这显著损害了图形表示的质量并限制了下游任务的性能。受大型语言模型 (LLM) 卓越的推理和上下文理解能力的推动，我们探索了使用 LLM 作为图边缘细化器的想法。具体来说，我们提出了一个两阶段框架：我们首先验证基于 LLM 的边缘细化可以有效识别和删除冗余连接，从而显著提高癫痫检测准确性和更有意义的图结构。基于这一见解，我们进一步开发了一个强大的解决方案，其中使用基于 Transformer 的边缘预测器和多层感知器构建初始图，为潜在边缘分配概率分数并应用阈值来确定它们的存在。然后，LLM 充当边缘集细化器，根据节点对的文本和统计特征做出明智的决策，以验证剩余的连接。对 TUSZ 数据集的大量实验表明，我们的 LLM 改进的图形学习框架不仅提高了任务性能，而且还产生了更清晰、更可解释的图形表示。

## 核心贡献

- **首次将 LLM 用作图结构细化器**：探索了 LLM 在图结构学习中的新角色，利用其推理和上下文理解能力对图边缘进行精细化处理
- **两阶段框架设计**：提出"初始图构建 + LLM 边缘细化"的两阶段流程，先用 Transformer 预测器和 MLP 构建初始图，再由 LLM 精选边缘
- **基于多模态信息的边缘验证**：LLM 综合节点对的文本特征和统计特征进行边缘存在性判断，超越了纯数值相关性方法
- **提升可解释性**：LLM 细化后的图结构更清晰、更可解释，有利于临床理解

## 方法概述

该论文提出了一种将大语言模型 (LLM) 用作图结构细化器的新框架，用于改善脑电图 (EEG) 癫痫检测中的图表示学习。EEG 信号由于噪声大，基于相关性或学习的图构建方法容易产生冗余或不相关的边缘，严重影响图表示质量和下游任务性能。

框架分为两个阶段。第一阶段：初始图构建。使用基于 Transformer 的边缘预测器和多层感知器 (MLP) 对 EEG 通道对进行评分，为每个潜在边缘分配概率分数，并通过阈值确定边的存在与否。第二阶段：LLM 边缘细化。将初始图的节点对信息（包括文本描述和统计特征）输入 LLM，利用 LLM 的推理能力对边缘进行二次验证和筛选，移除冗余连接，保留有意义的结构关系。

该方法的核心创新在于利用 LLM 的上下文理解和推理能力来判断图边缘的合理性，而非仅仅依赖数值相关性。LLM 能够综合理解 EEG 通道间的语义关系和统计模式，做出更准确的边缘存在性判断。

## 实验结果

- **数据集**: TUSZ（颞叶癫痫手术数据集）
- **核心框架**: Transformer 边缘预测器 + MLP 初始图构建 → LLM 边缘细化
- **关键发现**:
  - LLM 边缘细化能有效识别和移除冗余连接
  - 癫痫检测准确性显著提升
  - 产生的图结构更清晰、更具可解释性
- **对比优势**: 相比纯相关性方法和纯学习方法，LLM 细化后的图在任务性能和结构质量上均有改善

## 相关概念

- [脑电图](../concepts/eeg.html)
- [图神经网络](../concepts/graph-neural-networks.html)
- [癫痫检测](../concepts/seizure-detection.html)
- [大语言模型](../concepts/large-language-models.html)
- [图结构学习](../concepts/graph-structure-learning.html)
- [临床 AI](../concepts/clinical-ai.html)

---

*导入时间: 2026-05-01 19:53*
*来源: arXiv Daily Digest 2026-05-01*
