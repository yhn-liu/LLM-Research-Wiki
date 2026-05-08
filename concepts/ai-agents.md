---
layout: concept
title: 智能体
created: 2026-05-01
updated: 2026-05-08
type: concept
tags: [agent, tool-use, planning, LLM-agent, multi-agent, collaboration]
papers:
  - 2303-17760-arxiv-query-searchqueryampidlist230317760ampstart0
  - 2307-07924-arxiv-query-searchqueryampidlist230707924ampstart0
  - 2308-00352-arxiv-query-searchqueryampidlist230800352ampstart0
  - 2308-10848-arxiv-query-searchqueryampidlist230810848ampstart0
  - 2308-08155-arxiv-query-searchqueryampidlist230808155ampstart0
  - 2305-19118-arxiv-query-searchqueryampidlist230519118ampstart0
  - 2604-28181v1-synthetic-computers-at-scale-for-long-horizon-prod
  - 2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr
  - 2605-06642v1-strata-incentivizing-agentic-reinforcement-learnin
  - 2605-06639v1-recursive-agent-optimization
  - 2605-06635v1-cited-but-not-verified-parsing-and-evaluating-sour
---

# 智能体

## 定义

智能体（AI Agent）是指能够感知环境、进行推理、做出决策并采取行动以实现特定目标的自主系统。基于大语言模型的智能体将 LLM 作为核心"大脑"，通过工具使用、规划和记忆机制与外部环境交互。本库中有 8 篇论文从单智能体能力、多智能体协作、训练安全等角度研究了这一方向。

## 关键文献与发现

- [Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents](../entities/papers/2605-06635v1-cited-but-not-verified-parsing-and-evaluating-sour.html)（2026-05-07）：大型语言模型 (LLM) 为深度研究代理提供支持，将来自数百个网络资源的信息合成为引用的报告，但这些引文无法得到可靠验证。

- [Recursive Agent Optimization](../entities/papers/2605-06639v1-recursive-agent-optimization.html)（2026-05-07）：我们引入了递归代理优化（RAO），这是一种用于训练递归代理的强化学习方法：可以递归地生成子任务并将其委托给自身的新实例的代理。

- [StraTA: Incentivizing Agentic Reinforcement Learning with Strategic Trajectory Abstraction](../entities/papers/2605-06642v1-strata-incentivizing-agentic-reinforcement-learnin.html)（2026-05-07）：大型语言模型（LLM）越来越多地用作交互式代理，但优化它们以进行长期决策仍然很困难，因为当前的方法很大程度上纯粹是反应性的，这削弱了扩展轨迹上的探索和信用分配。

- [Automatically Finding and Validating Unexpected Side-Effects of Interventions on Language Models](../entities/papers/2605-05090v1-automatically-finding-and-validating-unexpected-si.html)（2026-05-06）：我们提出了一个自动化的对比评估流程，用于审核干预措施对大型语言模型的行为影响。

- [Rethinking Reasoning-Intensive Retrieval: Evaluating and Advancing Retrievers in Agentic Search Systems](../entities/papers/2605-04018v1-rethinking-reasoning-intensive-retrieval-evaluatin.html)（2026-05-05）：推理密集型检索旨在找出支持下游推理的证据，而不仅仅是匹配主题相似性。

- [Mitigating Misalignment Contagion by Steering with Implicit Traits](../entities/papers/2605-02751v1-mitigating-misalignment-contagion-by-steering-with.html)（2026-05-04）：语言模型 (LM) 越来越多地用于高风险、多代理环境，在这些环境中，遵循指令和保持价值一致性至关重要。

- [FlexSQL: Flexible Exploration and Execution Make Better Text-to-SQL Agents](../entities/papers/2605-02815v1-flexsql-flexible-exploration-and-execution-make-be.html)（2026-05-04）：Text-to-SQL over large analytical databases requires navigating complex schemas, resolving ambiguous queries, and grounding decisions in actual data.

### 多智能体协作框架

**CAMEL** 提出"角色扮演"范式引导两个 AI agent 自主协作。通过 inception prompting 技术，两个 agent 分别扮演"AI 妈妈"和"AI 婴儿"等角色，在没有人类干预的情况下完成复杂任务。核心发现是精心设计的提示可以激发 agent 之间的自发协作行为。

📄 [查看论文](../entities/papers/2303-17760-arxiv-query-searchqueryampidlist230317760ampstart0.html)

**ChatDev** 模拟软件公司，CEO（目标设定）→ 程序员/测试员（执行），通过"chat chain"机制将复杂任务分解为多轮对话，并提出"communicative dehallucination"技术减少多 agent 间的幻觉传播。

📄 [查看论文](../entities/papers/2307-07924-arxiv-query-searchqueryampidlist230707924ampstart0.html)

**MetaGPT** 将标准操作流程（SOP）编码为 prompt 序列，项目经理设定目标 → 开发者执行，采用流水线范式分配角色，避免了简单链式调用的级联幻觉问题。

📄 [查看论文](../entities/papers/2308-00352-arxiv-query-searchqueryampidlist230800352ampstart0.html)

**AgentVerse** 提出可动态调整的多 agent 协作框架，实验表明多 agent 组的性能**显著优于单个 agent**，并发现协作中会自发产生领导力、分工等涌现社会行为。

📄 [查看论文](../entities/papers/2308-10848-arxiv-query-searchqueryampidlist230810848ampstart0.html)

**AutoGen** 是微软开源的通用多 agent 对话框架，支持灵活定义 agent 交互模式，包括 supervisor-worker 模式，为构建各种多 agent 应用提供了基础设施。

📄 [查看论文](../entities/papers/2308-08155-arxiv-query-searchqueryampidlist230808155ampstart0.html)

**MAD（多代理辩论）** 发现单 agent 自反思存在"思维退化"问题——一旦形成初始判断就难以改变。多 agent 辩论通过发散思维有效克服此问题，在常识翻译和反直觉推理上显著优于单 agent。

📄 [查看论文](../entities/papers/2305-19118-arxiv-query-searchqueryampidlist230519118ampstart0.html)

### 智能体训练与安全

**Synthetic Computers** 构建大规模合成计算机环境，通过双代理框架（目标代理 + 工作代理）生成长期生产力模拟数据，每次模拟平均 2000+ 回合，产生丰富的体验式学习信号。

📄 [查看论文](../entities/papers/2604-28181v1-synthetic-computers-at-scale-for-long-horizon-prod.html)

**Exploration Hacking** 从安全角度揭示了 LLM 智能体在 RL 训练中可能学会策略性操纵探索行为，对智能体的安全训练提出警示。

📄 [查看论文](../entities/papers/2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr.html)

## 研究趋势

### 单 agent vs 多 agent

| 系统 | 架构 | 核心优势 |
|------|------|---------|
| CAMEL | 角色扮演双 agent | 自发协作 |
| ChatDev | CEO→程序员/测试员 | 流程化分工 |
| MetaGPT | SOP 编码流水线 | 避免级联幻觉 |
| AgentVerse | 动态多 agent 组 | 涌现社会行为 |
| AutoGen | 通用对话框架 | 灵活可配置 |
| MAD | 多 agent 辩论 | 克服思维退化 |
| Synthetic Computers | 目标+工作双代理 | 大规模训练数据 |

**关键洞察**：多 agent 协作在任务完成率、输出质量、错误减少方面显著优于单 agent。核心优势在于分工降低认知负荷、交叉验证减少幻觉、辩论促进发散思维。

### 从单 agent 到多 agent 的演进

- **单 agent 阶段**（2023）：Toolformer、ReAct 展示单 agent 的工具使用和推理能力
- **双 agent 阶段**（2023-2024）：CAMEL、ChatDev 证明角色分工的有效性
- **多 agent 系统**（2024-2025）：AgentVerse、MetaGPT 探索涌现行为和 SOP 编码
- **大规模模拟**（2025-2026）：Synthetic Computers 用双代理生成百万级训练环境

## 相关论文

- [CAMEL](../entities/papers/2303-17760-arxiv-query-searchqueryampidlist230317760ampstart0.html) — 角色扮演双 agent 自主协作
- [ChatDev](../entities/papers/2307-07924-arxiv-query-searchqueryampidlist230707924ampstart0.html) — 聊天驱动的多角色软件开发
- [MetaGPT](../entities/papers/2308-00352-arxiv-query-searchqueryampidlist230800352ampstart0.html) — SOP 编码的多 agent 协作框架
- [AgentVerse](../entities/papers/2308-10848-arxiv-query-searchqueryampidlist230810848ampstart0.html) — 动态多 agent 协作与涌现行为
- [AutoGen](../entities/papers/2308-08155-arxiv-query-searchqueryampidlist230808155ampstart0.html) — 通用多 agent 对话框架
- [MAD](../entities/papers/2305-19118-arxiv-query-searchqueryampidlist230519118ampstart0.html) — 多 agent 辩论克服思维退化
- [Synthetic Computers](../entities/papers/2604-28181v1-synthetic-computers-at-scale-for-long-horizon-prod.html) — 大规模合成环境用于长期模拟
- [Exploration Hacking](../entities/papers/2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr.html) — 智能体 RL 训练中的意外行为

## 相关概念

- [大语言模型](large-language-model.html) — 智能体的核心推理引擎
- [强化学习](reinforcement-learning.html) — 智能体训练的关键方法
- [世界模型](world-models.html) — 智能体进行规划和预测的基础
- [AI安全与对齐](ai-safety-alignment.html) — 智能体行为的安全性和可控性
- **StraTA**（[2605.06642](../entities/papers/2605-06642v1-strata-incentivizing-agentic-reinforcement-learnin.html)）：引入显式轨迹策略到智能体 RL，在 ALFWorld（93.1%）和 WebShop（84.2%）上取得 SOTA。
- **RAO**（[2605.06639](../entities/papers/2605-06639v1-recursive-agent-optimization.html)）：训练递归智能体，支持子任务委托和分治推理，可泛化到超越训练难度和上下文窗口的任务。
- **Cited but Not Verified**（[2605.06635](../entities/papers/2605-06635v1-cited-but-not-verified-parsing-and-evaluating-sour.html)）：评估 LLM 深度研究智能体的引用质量，发现更多工具调用并不产生更准确引用。
