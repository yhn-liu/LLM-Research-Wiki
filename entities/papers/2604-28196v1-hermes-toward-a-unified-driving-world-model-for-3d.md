---
layout: paper
title: "HERMES++: Toward a Unified Driving World Model for 3D Scene Understanding and Generation"
arxiv_id: 2604.28196v1
authors: ""
published: 2026-05-01
categories: cs.CV
tags: [cv]
type: paper
source_url: https://arxiv.org/abs/2604.28196v1
pdf_url: https://arxiv.org/pdf/2604.28196v1
---


# HERMES++: Toward a Unified Driving World Model for 3D Scene Understanding and Generation

## 基本信息

- **arXiv ID:** [2604.28196v1](https://arxiv.org/abs/2604.28196v1)
- **作者:** Xin Zhou, Dingkang Liang, Xiwu Chen et al. (7 authors)
- **发布日期:** 2026-04-30
- **分类:** cs.CV

## 摘要

### English

Driving world models serve as a pivotal technology for autonomous driving by simulating environmental dynamics. However, existing approaches predominantly focus on future scene generation, often overlooking comprehensive 3D scene understanding. Conversely, while Large Language Models (LLMs) demonstrate impressive reasoning capabilities, they lack the capacity to predict future geometric evolution, creating a significant disparity between semantic interpretation and physical simulation. To bridge

### 中文

驾驶世界模型通过模拟环境动态，成为自动驾驶的关键技术。然而，现有方法主要关注未来场景生成，往往忽视全面的 3D 场景理解。相反，虽然大型语言模型（LLM）表现出令人印象深刻的推理能力，但它们缺乏预测未来几何演化的能力，从而在语义解释和物理模拟之间造成了显着差异。为了弥补这一差距，我们提出了 HERMES++，这是一种统一的驾驶世界模型，它将 3D 场景理解和未来几何预测集成在一个框架内。我们的方法通过协同设计满足这些任务的独特要求。首先，BEV 表示将多视图空间信息整合到与 LLM 兼容的结构中。其次，我们引入了 LLM 增强的世界查询，以促进理解分支的知识转移。第三，当前到未来的链接旨在弥合时间差距，根据语义上下文调节几何演化。最后，为了加强结构完整性，我们采用联合几何优化策略，该策略将显式几何约束与隐式潜在正则化相结合，以使内部表示与几何感知先验保持一致。对多个基准的广泛评估验证了我们方法的有效性。 HERMES++ 实现了强大的性能，在未来点云预测和 3D 场景理解任务中均优于专业方法。模型和代码将在https://github.com/H-EmbodVis/HERMESV2公开

## 核心贡献

- ### English

Driving world models serve as a pivotal technology for autonomous driving by simulating environmental dynamics

## 方法概述

es predominantly focus on future scene generation, often overlooking comprehensive 3D scene understanding.  Conversely, while Large Language Models (LLMs) demonstrate impressive reasoning capabilities, they lack the capacity to predict future geometric evolution, creating a significant disparity between semantic interpretation and physical simulation.  To bridge this gap, we propose H ERMES ++, a unified driving world model that integrates 3D scene understanding and future geometry prediction with.

## 实验结果

impressive reasoning capabilities

## 相关论文

<!-- 待填充：添加相关论文链接 -->


## 分析信息

- **分析来源:** summary_extract
- **分析置信度:** medium
- **分析时间:** 2026-05-01 20:14
- **关键词:** LLM, large language model, RL, generation


## 分析信息

- **分析来源:** pdf_analysis
- **分析置信度:** high
- **分析时间:** 2026-05-01 20:20
- **关键词:** LLM, large language model, RL, generation, 3D
- **PDF 路径:** /root/wiki/raw/papers/2604-28196v1.pdf

---
*导入时间: 2026-05-01 19:53*
*来源: arXiv Daily Digest 2026-05-01*
