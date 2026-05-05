---
layout: paper
title: "Reinforcement Learning for LLM-based Multi-Agent Systems through Orchestration Traces"
created: 2026-05-05
updated: 2026-05-05
type: paper
arxiv_id: 2605.02801v1
authors: "Chenchen Zhang"
published: 2026-05-04
categories: cs.CL
tags: [nlp]
source_url: https://arxiv.org/abs/2605.02801v1
pdf_url: https://arxiv.org/pdf/2605.02801v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: []
---

# Reinforcement Learning for LLM-based Multi-Agent Systems through Orchestration Traces

## 基本信息

- **arXiv ID:** [2605.02801v1](https://arxiv.org/abs/2605.02801v1)
- **作者:** Chenchen Zhang
- **发布日期:** 2026-05-04
- **分类:** cs.CL
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2605.02801v1)


## 摘要

### English

As large language model (LLM) agents evolve from isolated tool users into coordinated teams, reinforcement learning (RL) must optimize not only individual actions but also how work is spawned, delegated, communicated, aggregated, and stopped. This paper studies RL for LLM-based multi-agent systems through orchestration traces: temporal interaction graphs whose events include sub-agent spawning, delegation, communication, tool use, return, aggregation, and stopping decisions. Using this lens, we identify three technical axes. First, reward design spans eight families, including orchestration rewards for parallelism speedup, split correctness, and aggregation quality. Second, reward and credit signals attach to eight credit- or signal-bearing units from token to team; explicit counterfactual message-level credit remains especially sparse in our curated pool. Third, orchestration learning decomposes into five sub-decisions: when to spawn, whom to delegate to, how to communicate, how to aggregate, and when to stop. In our curated pool as of May 4, 2026, we found no explicit RL training method for the stopping decision. We connect academic methods to public industrial evidence from Kimi Agent Swarm, OpenAI Codex, and Anthropic Claude Code. The resulting scale gap is a gap between publicly reported deployment envelopes and open academic evaluation regimes, not independent verification of industrial training traces. We release the artifact at https://github.com/xxzcc/awesome-llm-mas-rl, including an 84-entry tagged paper pool, a 32-record exclusion log, scripted corpus statistics, and a minimal JSON schema for replayable orchestration traces.

### 中文

随着大语言模型智能体从孤立的工具用户发展为协调的团队，强化学习不仅需要优化个体行为，还必须优化工作的生成、委托、通信、聚合和停止方式。本文通过编排轨迹（orchestration traces）研究基于 LLM 的多智能体系统的强化学习：编排轨迹是时间交互图，其事件包括子智能体生成、委托、通信、工具使用、返回、聚合和停止决策。通过这一视角，我们识别出三个技术维度。第一，奖励设计涵盖八类，包括并行加速、拆分正确性和聚合质量的编排奖励。第二，奖励与信用信号可附加到从 token 到团队的八个信号承载单元；显式的反事实消息级信用在现有文献中尤为稀疏。第三，编排学习分解为五个子决策：何时生成、委托给谁、如何通信、如何聚合以及何时停止。截至 2026 年 5 月 4 日，在策划的文献池中未发现针对停止决策的显式 RL 训练方法。我们将学术方法与 Kimi Agent Swarm、OpenAI Codex 和 Anthropic Claude Code 的公开工业证据联系起来，揭示出公开部署范围与开放学术评估之间的规模差距。我们发布了包含 84 条目文献池、32 条排除日志和最小 JSON schema 的开源资源。

## 核心贡献

1. **编排轨迹框架**：首次将多智能体系统的 RL 优化形式化为编排轨迹（orchestration traces）——涵盖子智能体生成、委托、通信、聚合和停止的事件图，为多智能体 RL 提供了统一的抽象。
2. **三维度系统化分析**：从奖励设计（8 类）、信用分配（8 个信号承载单元）、编排学习（5 个子决策）三个维度系统梳理现有方法，识别出关键空白（如消息级反事实信用、停止决策的 RL 训练）。
3. **工业-学术界差距实证**：通过连接学术方法与 Kimi Agent Swarm、OpenAI Codex、Anthropic Claude Code 的公开工业证据，揭示了部署规模与学术评估之间的差距，为后续研究提供了方向性指引。
4. **开放资源发布**：提供 84 条目文献池、32 条排除日志、语料库统计和可重播编排轨迹的 JSON schema。

## 方法概述

本文是一篇**综述/立场论文（survey/position paper）**，主要方法为系统文献梳理和概念框架构建：

- **编排轨迹定义**：将多智能体交互建模为时间交互图 G = (V, E)，其中节点 V 为智能体/工具，边 E 为交互事件。事件类型包括：spawn（生成子智能体）、delegate（委托任务）、communicate（通信）、tool_use（工具使用）、return（返回结果）、aggregate（聚合结果）、stop（停止决策）。
- **三维度分析框架**：
  1. **奖励设计（Reward Design）**：八类奖励（任务完成、并行加速、拆分正确性、聚合质量、通信效率、资源消耗、安全合规、端到端性能）。
  2. **信用分配（Credit Assignment）**：八个信号承载级别（token 级、消息级、步骤级、子任务级、智能体级、子团队级、团队级、轨迹级）。发现消息级反事实信用特别稀疏。
  3. **编排学习（Orchestration Learning）**：五个子决策（spawn/delegate/communicate/aggregate/stop），发现停止决策无显式 RL 训练方法。
- **文献收集**：通过关键词检索 arXiv、ACL、NeurIPS、ICML 等来源，筛选出 84 篇相关论文，记录 32 篇排除论文及原因。

## 实验结果

本文为综述论文，无传统实验。主要发现包括：

- **停止决策空白**：截至 2026 年 5 月 4 日，无任何论文提出针对多智能体系统"何时停止"的显式 RL 训练方法。
- **消息级信用稀疏**：绝大多数信用分配方法停留在智能体级或步骤级，消息级反事实信用极少数工作涉及。
- **工业-学术规模差距**：Kimi Agent Swarm 声称数千智能体协调、Claude Code 和 OpenAI Codex 支持复杂多智能体工作流，但学术评估多在 2-5 个智能体、简单任务上。
- **奖励设计碎片化**：八类奖励在文献中分布不均，编排相关奖励（并行加速、聚合质量）关注度不足。

## 局限性与注意点

- **非系统性综述**：本文是精选文献池而非系统性综述，覆盖率有限（84 篇入选、32 篇排除）。
- **工业证据间接性**：工业系统的分析基于公开报告和推断，非独立验证的训练轨迹。
- **快速演变领域**：截至 2026 年 5 月的快照，多智能体 RL 领域进展迅速，文献池可能快速过时。
- **无实验验证**：框架性贡献无实验验证，提出的空白（如停止决策 RL）尚待实际方法填补。

## 相关概念（详细）

- **多智能体强化学习 (Multi-Agent RL)**：多智能体系统中的 RL 优化，核心挑战包括信用分配、协调学习和可扩展性。本文通过编排轨迹视角重新组织该领域。
- **编排学习 (Orchestration Learning)**：本文引入的概念，涵盖 spawn/delegate/communicate/aggregate/stop 五个子决策的联合优化。
- **信用分配 (Credit Assignment)**：确定每个智能体/行为对全局奖励贡献的机制，消息级反事实信用是本文识别的重要空白。

## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [强化学习](../../concepts/reinforcement-learning.html)
- [基准评估](../../concepts/benchmarking.html)
- [图神经网络](../../concepts/graph-neural-networks.html)

---
*导入时间: 2026-05-05 06:01*
*来源: arXiv Daily Wiki Update 2026-05-05*
