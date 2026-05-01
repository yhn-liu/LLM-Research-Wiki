---
layout: paper
title: "LLM as Clinical Graph Structure Refiner: Enhancing Representation Learning in EEG Seizure Diagnosis"
arxiv_id: 
authors: ""
published: 
categories: 
tags: []
type: paper
source_url: https://arxiv.org/abs/
pdf_url: https://arxiv.org/pdf/
---

# LLM as Clinical Graph Structure Refiner: Enhancing Representation Learning in EEG Seizure Diagnosis

## 基本信息

- **arXiv ID:** [2604.28178v1](https://arxiv.org/abs/2604.28178v1)
- **作者:** Lincan Li, Zheng Chen, Yushun Dong
- **发布日期:** 2026-04-30
- **分类:** cs.AI

## 摘要

### English

Electroencephalogram (EEG) signals are vital for automated seizure detection, but their inherent noise makes robust representation learning challenging. Existing graph construction methods, whether correlation-based or learning-based, often generate redundant or irrelevant edges due to the noisy nature of EEG data. This significantly impairs the quality of graph representation and limits downstream task performance. Motivated by the remarkable reasoning and contextual understanding capabilities 

### 中文

脑电图 (EEG) 信号对于自动癫痫检测至关重要，但其固有的噪声使得稳健的表示学习具有挑战性。现有的图构建方法，无论是基于相关性的还是基于学习的，由于脑电图数据的噪声性质，通常会生成冗余或不相关的边缘。这显着损害了图形表示的质量并限制了下游任务的性能。受大型语言模型 (LLM) 卓越的推理和上下文理解能力的推动，我们探索了使用 LLM 作为图边缘细化器的想法。具体来说，我们提出了一个两阶段框架：我们首先验证基于LLM的边缘细化可以有效识别和删除冗余连接，从而显着提高癫痫检测准确性和更有意义的图结构。基于这一见解，我们进一步开发了一个强大的解决方案，其中使用基于 Transformer 的边缘预测器和多层感知器构建初始图，为潜在边缘分配概率分数并应用阈值来确定它们的存在。然后，LLM 充当边缘集细化器，根据节点对的文本和统计特征做出明智的决策，以验证剩余的连接。对 TUSZ 数据集的大量实验表明，我们的 LLM 改进的图形学习框架不仅提高了任务性能，而且还产生了更清晰、更可解释的图形表示。

## 核心贡献

- ### English

Electroencephalogram (EEG) signals are vital for automated seizure detection, but their inherent noise makes robust representation learning challenging

## 方法概述

s, whether correlation-based or learning-based, often generate redundant or irrelevant edges due to the noisy nature of EEG data.  This significantly impairs the quality of graph representation and limits downstream task performance.  Motivated by the remarkable reasoning and contextual understanding capabilities of large language models (LLMs), we explore the idea of using LLMs as graph edge refiners.

## 实验结果

that our LLM-refined graph learning framework not; that our LLM-refined graph learning framework not

## 相关论文

<!-- 待填充：添加相关论文链接 -->


## 分析信息

- **分析来源:** summary_extract
- **分析置信度:** medium
- **分析时间:** 2026-05-01 20:14
- **关键词:** AI, ML


## 分析信息

- **分析来源:** pdf_analysis
- **分析置信度:** high
- **分析时间:** 2026-05-01 20:20
- **关键词:** transformer, attention, LLM, large language model, MLP, RL, generation
- **PDF 路径:** /root/wiki/raw/papers/2604-28178v1.pdf

---
*导入时间: 2026-05-01 19:53*
*来源: arXiv Daily Digest 2026-05-01*
