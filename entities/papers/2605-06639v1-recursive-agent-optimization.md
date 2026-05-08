---
layout: paper
title: "Recursive Agent Optimization"
created: 2026-05-08
updated: 2026-05-08
type: paper
arxiv_id: 2605.06639v1
authors: "Apurva Gandhi, Satyaki Chakraborty, Xiangjun Wang, Aviral Kumar, Graham Neubig"
published: 2026-05-07
categories: cs.LG, cs.AI, cs.CL, cs.MA
tags: [ml, ai, nlp]
source_url: https://arxiv.org/abs/2605.06639v1
pdf_url: https://arxiv.org/pdf/2605.06639v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: []
---

# Recursive Agent Optimization

## 基本信息

- **arXiv ID:** [2605.06639v1](https://arxiv.org/abs/2605.06639v1)
- **作者:** Apurva Gandhi, Satyaki Chakraborty, Xiangjun Wang et al.
- **发布日期:** 2026-05-07
- **分类:** cs.LG, cs.AI, cs.CL, cs.MA
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2605.06639v1)


## 摘要

### English

We introduce Recursive Agent Optimization (RAO), a reinforcement learning approach for training recursive agents: agents that can spawn and delegate sub-tasks to new instantiations of themselves recursively. Recursive agents implement an inference-time scaling algorithm that naturally allows agents to scale to longer contexts and generalize to more difficult problems via divide-and-conquer. RAO provides a method to train models to best take advantage of such recursive inference, teaching agents when and how to delegate and communicate. We find that recursive agents trained in this way enjoy better training efficiency, can scale to tasks that go beyond the model's context window, generalize to tasks much harder than the ones the agent was trained on, and can enjoy reduced wall-clock time compared to single-agent systems.

### 中文

我们引入了递归代理优化（RAO），这是一种用于训练递归代理的强化学习方法：可以递归地生成子任务并将其委托给自身的新实例的代理。递归代理实现了推理时间缩放算法，该算法自然地允许代理扩展到更长的上下文，并通过分治法推广到更困难的问题。 RAO 提供了一种训练模型的方法，以最好地利用这种递归推理，指导代理何时以及如何进行委派和通信。我们发现，以这种方式训练的递归代理具有更好的训练效率，可以扩展到超出模型上下文窗口的任务，泛化到比代理训练的任务难得多的任务，并且与单代理系统相比可以减少挂钟时间。


## 核心贡献

### English
RAO introduces a reinforcement learning approach for training recursive agents — agents that can spawn and delegate sub-tasks to new instantiations of themselves recursively. This implements an inference-time scaling algorithm via divide-and-conquer: when facing a complex problem, a recursive agent can decompose it into sub-problems, spawn child agents to solve them, and aggregate results. RAO teaches models when and how to delegate and communicate through RL training. Key findings: recursive agents trained with RAO enjoy better training efficiency, can scale to tasks beyond the model's context window, generalize to tasks much harder than training tasks, and achieve reduced wall-clock time compared to single-agent systems.

### 中文
RAO 引入了一种用于训练递归智能体的强化学习方法——能够递归地生成子任务并委托给自身新实例的智能体。这通过分治法实现了推理时扩展算法：面对复杂问题时，递归智能体可以将其分解为子问题，生成子智能体来解决它们，并聚合结果。RAO 通过 RL 训练教会模型何时以及如何委托和通信。关键发现：用 RAO 训练的递归智能体具有更好的训练效率，可以扩展到超出模型上下文窗口的任务，泛化到比训练任务难得多的任务，并且与单智能体系统相比实现更少的挂钟时间。

## 方法概述

### English
RAO formulates recursive agent behavior as a reinforcement learning problem where the agent learns a policy for: (1) deciding whether to solve a sub-task directly or delegate it, (2) when delegating, defining the sub-task specification and communication protocol, and (3) aggregating results from child agents. The training uses a hierarchical RL objective where parent and child agents are instances of the same model. Rewards are based on task completion, with efficiency bonuses for effective delegation. The recursive structure allows the system to naturally handle problems that exceed single-call context limits by distributing work across multiple agent instances. Communication between parent and child agents follows a structured protocol (task description, context, expected output format). The policy is optimized using GRPO-style group-based training across recursive call trees.

### 中文
RAO 将递归智能体行为形式化为强化学习问题，智能体学习以下策略：(1) 决定直接解决子任务还是委托，(2) 委托时定义子任务规范和通信协议，(3) 聚合子智能体的结果。训练使用分级 RL 目标，父智能体和子智能体是同一模型的实例。奖励基于任务完成，有效委托有额外效率奖励。递归结构允许系统通过将工作分布到多个智能体实例来自然处理超出单次调用上下文限制的问题。父智能体和子智能体之间的通信遵循结构化协议（任务描述、上下文、预期输出格式）。策略使用 GRPO 式分组训练在递归调用树上优化。

## 实验结果

### English
RAO demonstrates: (1) Better training efficiency — recursive agents learn faster than non-recursive baselines on compositional tasks. (2) Context-window scaling — recursive agents successfully solve tasks that exceed the base model's native context window by distributing work. (3) Difficulty generalization — agents trained on easy compositional tasks generalize to much harder compositions without additional training. (4) Wall-clock improvements — parallel execution of independent sub-tasks reduces total completion time. (5) The delegation decision quality improves over training, with the model learning to identify suitable decomposition points.

### 中文
RAO 展示了：(1) 更好的训练效率——递归智能体在组合任务上比非递归基线学习更快。(2) 上下文窗口扩展——递归智能体通过分配工作成功解决超出基座模型原生上下文窗口的任务。(3) 难度泛化——在简单组合任务上训练的智能体无需额外训练即可泛化到更难组合。(4) 挂钟时间改进——独立子任务的并行执行减少总完成时间。(5) 委托决策质量随训练提升，模型学会识别合适的分解点。

## 局限性与注意点

### English
(1) Recursive decomposition quality depends heavily on the base model's reasoning capability — weak models may produce nonsensical sub-tasks. (2) The communication overhead between parent and child agents can become significant for deep recursion. (3) Error propagation: mistakes in child agents cascade upward, potentially compounding errors. (4) The approach has primarily been tested on reasoning and code tasks; generalizability to open-ended creative tasks is unclear. (5) Recursive spawning can lead to unbounded compute usage without careful termination conditions.

### 中文
(1) 递归分解质量高度依赖基座模型的推理能力——弱模型可能产生无意义的子任务。(2) 父子智能体间的通信开销在深度递归时可能显著。(3) 错误传播：子智能体的错误向上级联，可能复合错误。(4) 方法主要在推理和代码任务上测试；对开放式创造任务的泛化性不清楚。(5) 递归生成若无谨慎终止条件可能导致无界计算使用。

## 相关概念

- [强化学习](../../concepts/reinforcement-learning.html)
- [智能体](../../concepts/ai-agents.html)

---
*导入时间: 2026-05-08 06:02*
*来源: arXiv Daily Wiki Update 2026-05-08*
