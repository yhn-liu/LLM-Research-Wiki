---
layout: paper
title: "Synthetic Computers at Scale for Long-Horizon Productivity Simulation"
created: 2026-05-01
updated: 2026-05-01
type: paper
arxiv_id: 2604.28181v1
authors: "Tao Ge, Baolin Peng, Hao Cheng et al. (4 authors)"
published: 2026-04-30
categories: cs.AI, cs.CL, cs.LG
tags: [nlp, ml, ai]
source_url: https://arxiv.org/abs/2604.28181v1
pdf_url: https://arxiv.org/pdf/2604.28181v1
confidence: high
status: analyzed
---

# Synthetic Computers at Scale for Long-Horizon Productivity Simulation

## 基本信息

- **arXiv ID:** [2604.28181v1](https://arxiv.org/abs/2604.28181v1)
- **作者:** Tao Ge, Baolin Peng, Hao Cheng et al. (4 authors)
- **发布日期:** 2026-04-30
- **分类:** cs.AI, cs.CL, cs.LG

## 摘要

### English

Realistic long-horizon productivity work is strongly conditioned on user-specific computer environments, where much of the work context is stored and organized through directory structures and content-rich artifacts. To scale synthetic data creation for such productivity scenarios, we introduce Synthetic Computers at Scale, a scalable methodology for creating such environments with realistic folder hierarchies and content-rich artifacts (e.g., documents, spreadsheets, and presentations). Conditioned on each synthetic computer, we run long-horizon simulations: one agent creates computer-user-specific productivity goals requiring multiple specialized deliverables and approximately one month of human work; then, another agent acts as that user and continues working on the computer — e.g., navigating the filesystem for grounding, coordinating with simulated collaborators, and generating professional artifacts — until those goals are completed. In preliminary experiments, we create 1,000 synthetic computers and run long-horizon simulations on them; each run requires over 8 hours of agent wall-clock time and spans an average of over 2,000 turns. These simulations produce rich experiential learning signals, whose effectiveness is validated by significant improvements in agent performance on both in-domain and out-of-domain productivity evaluations. Given that personas are rich on the scale of billions, this approach can in principle scale to millions or even billions of synthetic user worlds with sufficient compute, enabling broader coverage across diverse occupations, roles, backgrounds, environments, and productivity needs.

### 中文

现实的长期生产力工作很大程度上取决于特定于用户的计算机环境，其中大部分工作上下文是通过目录结构和内容丰富的工件来存储和组织的。为了扩展此类生产力场景的合成数据创建，我们引入了大规模合成计算机，这是一种可扩展的方法，用于创建具有真实文件夹层次结构和内容丰富的工件（例如文档、电子表格和演示文稿）的此类环境。以每台合成计算机为条件，我们运行长期模拟：一个代理创建特定于计算机用户的生产力目标，需要多个专业交付成果和大约一个月的人工工作；然后，另一个代理充当该用户并继续在计算机上工作——例如，导航文件系统以进行接地、与模拟协作者协调以及生成专业工件——直到完成这些目标。在初步实验中，我们创建了 1,000 台合成计算机并对它们进行长期模拟；每次运行需要超过 8 个小时的代理运行时间，平均跨越 2,000 多个回合。这些模拟产生了丰富的体验式学习信号，其有效性通过域内和域外生产力评估的代理性能的显着改进得到了验证。鉴于人物角色在数十亿规模上非常丰富，这种方法原则上可以扩展到数百万甚至数十亿个具有足够计算能力的合成用户世界，从而更广泛地覆盖不同的职业、角色、背景、环境和生产力需求。我们认为，可扩展的合成计算机是通向真正有能力的生产力代理的有前途的路径。

## 核心贡献

- **提出 Synthetic Computers at Scale 方法论：** 一种可扩展的方法，用于创建具有真实文件夹层次结构和内容丰富工件（文档、电子表格、演示文稿等）的合成计算机环境，模拟真实用户的工作场景。
- **构建长期模拟框架：** 设计了双代理模拟流程——一个代理设定生产力目标，另一个代理作为虚拟用户在合成计算机上持续工作以完成目标，每次模拟平均超过2,000个交互回合。
- **验证体验式学习信号的有效性：** 通过域内和域外生产力评估，证明长期模拟能产生丰富的学习信号，显著提升代理性能。
- **展示大规模可扩展性潜力：** 证明该方法可利用数十亿规模的人物角色扩展到数百万甚至数十亿个合成用户世界，覆盖广泛的职业和生产力需求。

## 方法概述

本文提出了一种名为 Synthetic Computers at Scale 的可扩展方法论，核心思路是在计算机中构建模拟的用户工作环境。每台合成计算机都包含逼真的文件夹层次结构和多样化的内容丰富工件，如文档、电子表格和演示文稿等，从而还原真实用户的生产力工作场景。

在此基础上，研究者设计了一个双代理长期模拟框架。第一个代理负责根据合成计算机的特征，创建需要多个专业交付成果的生产力目标，这些目标模拟大约一个月的人工工作量。第二个代理则扮演该计算机用户的角色，在环境中持续工作——包括浏览文件系统获取上下文、与模拟协作者协调沟通、以及生成专业工件——直到完成所有设定的目标。

该方法的关键优势在于其可扩展性。由于人物角色数据在互联网上极为丰富（数十亿规模），合成计算机可以通过丰富的人物角色来大规模生成，从而实现对不同职业、角色、背景和工作环境的广泛覆盖。每次模拟运行需要超过8小时的代理运行时间，产生丰富的体验式学习信号用于训练。

## 实验结果

- **模拟规模：** 创建了 1,000 台合成计算机并运行长期模拟，每次运行需要超过 8 小时的代理运行时间，平均跨越超过 2,000 个交互回合
- **性能提升：** 模拟产生的体验式学习信号在域内和域外生产力评估中均带来代理性能的显著改进
- **可扩展性：** 方法可扩展至数百万甚至数十亿个合成用户世界，覆盖多样化的生产力场景

## 分析信息

- **分析来源:** pdf_analysis
- **分析置信度:** high
- **分析时间:** 2026-05-01 20:20
- **关键词:** 合成数据, 长期模拟, 代理训练, 生产力评估
- **PDF 路径:** /root/wiki/raw/papers/2604-28181v1.pdf

---
*导入时间: 2026-05-01 19:53*
*来源: arXiv Daily Digest 2026-05-01*

## 相关概念

- [合成数据](../concepts/synthetic-data.html)
- [强化学习](../concepts/reinforcement-learning.html)
- [大语言模型](../concepts/large-language-models.html)
- [代理能力](../concepts/agent-capabilities.html)
- [长期推理](../concepts/long-horizon-reasoning.html)
