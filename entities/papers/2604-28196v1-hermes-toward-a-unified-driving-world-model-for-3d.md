---
layout: paper
title: "HERMES++: Toward a Unified Driving World Model for 3D Scene Understanding and Generation"
created: 2026-05-01
updated: 2026-05-01
type: paper
arxiv_id: 2604.28196v1
authors: "Xin Zhou, Dingkang Liang, Xiwu Chen et al. (7 authors)"
published: 2026-04-30
categories: cs.CV
tags: [cv]
source_url: https://arxiv.org/abs/2604.28196v1
pdf_url: https://arxiv.org/pdf/2604.28196v1
confidence: high
status: analyzed
---

# HERMES++: Toward a Unified Driving World Model for 3D Scene Understanding and Generation

## 基本信息

- **arXiv ID:** [2604.28196v1](https://arxiv.org/abs/2604.28196v1)
- **作者:** Xin Zhou, Dingkang Liang, Xiwu Chen et al. (7 authors)
- **发布日期:** 2026-04-30
- **分类:** cs.CV

## 摘要

### English

Driving world models serve as a pivotal technology for autonomous driving by simulating environmental dynamics. However, existing approaches predominantly focus on future scene generation, often overlooking comprehensive 3D scene understanding. Conversely, while Large Language Models (LLMs) demonstrate impressive reasoning capabilities, they lack the capacity to predict future geometric evolution, creating a significant disparity between semantic interpretation and physical simulation. To bridge this gap, we propose HERMES++, a unified driving world model that integrates 3D scene understanding and future geometry prediction within a single framework. Our approach addresses these tasks through co-design that accommodates their distinct requirements. First, BEV representation aggregates multi-view spatial information into an LLM-compatible structure. Second, we introduce LLM-enhanced world queries to facilitate knowledge transfer in the understanding branch. Third, current-to-future links are designed to bridge the temporal gap, modulating geometric evolution based on semantic context. Finally, to enforce structural integrity, we adopt a joint geometric optimization strategy that combines explicit geometric constraints with implicit latent regularization to align internal representations with geometry-aware priors. Extensive evaluation across multiple benchmarks validates the effectiveness of our approach. HERMES++ achieves strong performance, outperforming specialized methods in both future point cloud prediction and 3D scene understanding tasks. Models and code will be publicly available at https://github.com/H-EmbodVis/HERMESV2.

### 中文

驾驶世界模型通过模拟环境动态，成为自动驾驶的关键技术。然而，现有方法主要关注未来场景生成，往往忽视全面的 3D 场景理解。相反，虽然大型语言模型（LLM）表现出令人印象深刻的推理能力，但它们缺乏预测未来几何演化的能力，从而在语义解释和物理模拟之间造成了显着差异。为了弥补这一差距，我们提出了 HERMES++，这是一种统一的驾驶世界模型，它将 3D 场景理解和未来几何预测集成在一个框架内。我们的方法通过协同设计满足这些任务的独特要求。首先，BEV 表示将多视图空间信息整合到与 LLM 兼容的结构中。其次，我们引入了 LLM 增强的世界查询，以促进理解分支的知识转移。第三，当前到未来的链接旨在弥合时间差距，根据语义上下文调节几何演化。最后，为了加强结构完整性，我们采用联合几何优化策略，该策略将显式几何约束与隐式潜在正则化相结合，以使内部表示与几何感知先验保持一致。对多个基准的广泛评估验证了我们方法的有效性。HERMES++ 实现了强大的性能，在未来点云预测和 3D 场景理解任务中均优于专业方法。模型和代码将在https://github.com/H-EmbodVis/HERMESV2公开。

## 核心贡献

- **提出统一的驾驶世界模型 HERMES++：** 首次将 3D 场景理解与未来几何预测集成在单一框架中，弥合了语义解释与物理模拟之间的差距。
- **设计 BEV 表示与 LLM 兼容的架构：** 通过 BEV（鸟瞰图）表示将多视图空间信息聚合为与 LLM 兼容的结构，实现空间信息与语言模型的有效对接。
- **引入 LLM 增强的世界查询机制：** 在理解分支中利用 LLM 增强的世界查询促进知识转移，提升场景理解能力。
- **提出当前到未来链接与联合几何优化策略：** 通过时间链接根据语义上下文调节几何演化，并采用显式几何约束与隐式潜在正则化相结合的联合优化策略，确保内部表示与几何感知先验的一致性。

## 方法概述

HERMES++ 是一种统一的驾驶世界模型，旨在同时解决 3D 场景理解和未来几何预测两大任务。其核心设计理念是通过协同设计（co-design）来满足这两个任务各自独特的需求，而非分别使用独立的模型。

在架构层面，HERMES++ 首先采用 BEV（鸟瞰图）表示作为统一的中间表示，将来自多个摄像头视角的空间信息聚合到与 LLM 兼容的结构中。这一设计使得多视图的空间信息能够被 LLM 高效处理。在此基础上，系统引入了 LLM 增强的世界查询（world queries），用于理解分支中的知识转移，使模型能够从语言模型的推理能力中获益。

为了连接当前场景理解和未来几何预测，HERMES++ 设计了"当前到未来链接"（current-to-future links）机制，根据语义上下文来调节几何演化过程。此外，为确保生成结果的结构完整性，模型采用了联合几何优化策略，将显式几何约束（如点云的几何结构）与隐式潜在正则化相结合，使内部表示与几何感知先验保持一致，从而在语义理解和几何生成之间实现有效协同。

## 实验结果

- **全面超越专业方法：** 在未来点云预测和 3D 场景理解任务中均优于各自领域的专业方法
- **多基准验证：** 在多个基准测试上进行了广泛评估，验证了方法的有效性和泛化能力
- **统一框架优势：** 单一模型同时处理理解和生成任务，展现了统一架构相比独立模型的协同效应

## 分析信息

- **分析来源:** pdf_analysis
- **分析置信度:** high
- **分析时间:** 2026-05-01 20:20
- **关键词:** 驾驶世界模型, 3D场景理解, 点云预测, LLM
- **PDF 路径:** /root/wiki/raw/papers/2604-28196v1.pdf


## 分析信息

- **分析来源:** pdf_analysis
- **分析置信度:** high
- **分析时间:** 2026-05-02 06:02
- **关键词:** LLM, large language model, RL, generation, 3D
- **PDF 路径:** /root/wiki/raw/papers/2604-28196v1.pdf

---
*导入时间: 2026-05-01 19:53*
*来源: arXiv Daily Digest 2026-05-01*

## 相关概念

- [驾驶世界模型](../../concepts/driving-world-model.html)
- [3D场景理解](../../concepts/3d-scene-understanding.html)
- [大语言模型](../../concepts/large-language-models.html)
- [点云预测](../../concepts/point-cloud-prediction.html)
- [BEV表示](../../concepts/bev-representation.html)
- [自动驾驶](../../concepts/autonomous-driving.html)
