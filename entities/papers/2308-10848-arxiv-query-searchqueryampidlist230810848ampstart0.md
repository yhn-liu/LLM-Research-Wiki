---
layout: paper
title: "AgentVerse: Facilitating Multi-Agent Collaboration and Exploring Emergent Behaviors"
created: 2026-05-01
updated: 2026-05-01
type: paper
arxiv_id: 2308.10848
authors: "Weize Chen, Yusheng Su, Jingwei Zuo, Cheng Yang, Chenfei Yuan, Chi-Min Chan, Heyang Yu, Yaxi Lu, Yi-Hsin Hung, Chen Qian, Yujia Qin, Xin Cong, Ruobing Xie, Zhiyuan Liu, Maosong Sun, Jie Zhou"
published: 2026-05-01
categories: cs.CL, cs.CL
tags: [nlp]
source_url: https://arxiv.org/abs/2308.10848
pdf_url: https://arxiv.org/pdf/2308.10848
source_type: url
confidence: high
status: analyzed
---

# AgentVerse: Facilitating Multi-Agent Collaboration and Exploring Emergent Behaviors

## 基本信息

- **arXiv ID:** [2308.10848](https://arxiv.org/abs/2308.10848)
- **作者:** Weize Chen, Yusheng Su, Jingwei Zuo, Cheng Yang, Chenfei Yuan, Chi-Min Chan, Heyang Yu, Yaxi Lu, Yi-Hsin Hung, Chen Qian, Yujia Qin, Xin Cong, Ruobing Xie, Zhiyuan Liu, Maosong Sun, Jie Zhou
- **分类:** cs.CL, cs.CL
- **导入类型:** url

## 摘要

Autonomous agents empowered by Large Language Models (LLMs) have undergone significant improvements, enabling them to generalize across a broad spectrum of tasks. However, in real-world scenarios, cooperation among individuals is often required to enhance the efficiency and effectiveness of task accomplishment. Hence, inspired by human group dynamics, we propose a multi-agent framework \framework that can collaboratively and dynamically adjust its composition as a greater-than-the-sum-of-its-parts system. Our experiments demonstrate that \framework framework can effectively deploy multi-agent groups that outperform a single agent. Furthermore, we delve into the emergence of social behaviors among individual agents within a group during collaborative task accomplishment. In view of these behaviors, we discuss some possible strategies to leverage positive ones and mitigate negative ones for improving the collaborative potential of multi-agent groups. Our codes for \framework will soon be released at \url{https://github.com/OpenBMB/AgentVerse}.

## 核心贡献

1. **提出 AgentVerse 多智能体协作框架**：受人类群体动力学启发，构建了一个能够动态调整自身组成的多智能体协作系统，实现"整体大于部分之和"的效果。
2. **动态智能体团队构建**：框架支持根据任务需求动态招募、筛选和调整智能体团队成员，而非使用固定团队。
3. **涌现社会行为的发现与分析**：深入研究了多智能体在协作完成任务过程中涌现出的社会行为，包括正向（如协作、共识形成）和负向（如从众效应、说服偏差）行为。
4. **正负向行为的调控策略**：针对涌现的社会行为，提出了利用正向行为、抑制负向行为的策略，以提升多智能体群体的协作潜力。
5. **开源发布**：框架代码开源于 GitHub（OpenBMB/AgentVerse），便于社区复用和扩展。

## 方法概述

AgentVerse 框架包含四个核心阶段的协作流程：

1. **专家招募（Expert Recruitment）**：根据任务需求，从候选池中动态招募具备相关能力的 LLM 智能体，形成初始团队。
2. **观点协商（Collaborative Decision-Making）**：智能体之间通过多轮对话进行讨论，各自表达观点并协商，逐步收敛形成团队共识。
3. **行动执行（Action Execution）**：基于协商结果，各智能体分工执行具体任务操作（如代码生成、信息检索等）。
4. **评估与调整（Evaluation & Adjustment）**：对执行结果进行评估，决定是否需要调整团队组成或重新执行，形成闭环。

整个框架以 LLM 作为各智能体的推理引擎，通过结构化的多轮对话协议实现协作。框架支持灵活定义智能体角色和交互模式，适用于多种应用场景。

## 实验结果

实验在多个任务场景下验证了 AgentVerse 的有效性：

- **多智能体协作优于单智能体**：在知识密集型任务（如问答、推理）中，AgentVerse 部署的多智能体团队显著优于单个 LLM 智能体的表现，验证了协作的增益效果。
- **动态团队构建的优势**：与固定团队相比，动态招募和调整团队成员的策略能够更好地匹配任务需求，提升整体性能。
- **涌现行为的实证分析**：实验观察到智能体群体中确实会涌现社会行为，包括：
  - **正向行为**：如角色专业化分工、知识互补、共识形成等。
  - **负向行为**：如从众效应（conformity）、说服偏差（persuasion bias）等，可能导致群体思维退化。
- **调控策略有效性**：通过引入适当的辩论机制和评估反馈，可以有效抑制负向行为，提升协作质量。

## 相关概念

- [智能体](../../concepts/ai-agents.html)
- [大语言模型](../../concepts/large-language-model.html)


## 分析信息

- **分析来源:** pdf_analysis
- **分析置信度:** high
- **分析时间:** 2026-05-02 06:02
- **关键词:** GPT, LLM, large language model, RL
- **PDF 路径:** /root/wiki/raw/papers/2308-10848.pdf

---
*导入时间: 2026-05-01 23:30*
*导入方式: url*
