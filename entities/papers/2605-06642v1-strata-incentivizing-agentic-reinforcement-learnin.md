---
layout: paper
title: "StraTA: Incentivizing Agentic Reinforcement Learning with Strategic Trajectory Abstraction"
created: 2026-05-08
updated: 2026-05-08
type: paper
arxiv_id: 2605.06642v1
authors: "Xiangyuan Xue, Yifan Zhou, Zidong Wang, Shengji Tang, Philip Torr, Wanli Ouyang, Lei Bai, Zhenfei Yin"
published: 2026-05-07
categories: cs.CL, cs.AI
tags: [nlp, ai]
source_url: https://arxiv.org/abs/2605.06642v1
pdf_url: https://arxiv.org/pdf/2605.06642v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: []
---

# StraTA: Incentivizing Agentic Reinforcement Learning with Strategic Trajectory Abstraction

## 基本信息

- **arXiv ID:** [2605.06642v1](https://arxiv.org/abs/2605.06642v1)
- **作者:** Xiangyuan Xue, Yifan Zhou, Zidong Wang et al.
- **发布日期:** 2026-05-07
- **分类:** cs.CL, cs.AI
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2605.06642v1)


## 摘要

### English

Large language models (LLMs) are increasingly used as interactive agents, but optimizing them for long-horizon decision making remains difficult because current methods are largely purely reactive, which weakens both exploration and credit assignment over extended trajectories. In this work, we present Strategic Trajectory Abstraction (StraTA), a simple framework that introduces an explicit trajectory-level strategy into agentic reinforcement learning (RL). StraTA samples a compact strategy from the initial task state, conditions subsequent actions on that strategy, and trains strategy generation and action execution jointly with a hierarchical GRPO-style rollout design, further enhanced by diverse strategy rollout and critical self-judgment. Experiments on ALFWorld, WebShop, and SciWorld show that StraTA consistently improves both sample efficiency and final performance over strong baselines. StraTA reaches success rates of 93.1% on ALFWorld and 84.2% on WebShop. On SciWorld, StraTA attains a 63.5% overall score, outperforming frontier closed-source models.

### 中文

大型语言模型（LLM）越来越多地用作交互式代理，但优化它们以进行长期决策仍然很困难，因为当前的方法很大程度上纯粹是反应性的，这削弱了扩展轨迹上的探索和信用分配。在这项工作中，我们提出了策略轨迹抽象（StraTA），这是一个简单的框架，它将显式轨迹级策略引入代理强化学习（RL）中。 StraTA 从初始任务状态中采样紧凑策略，根据该策略调整后续操作，并与分层 GRPO 式推出设计联合训练策略生成和操作执行，并通过多样化策略推出和关键自我判断进一步增强。 ALFWorld、WebShop 和 SciWorld 上的实验表明，与强大的基线相比，StraTA 持续提高了样本效率和最终性能。 StraTA 在 ALFWorld 上的成功率达到 93.1%，在 WebShop 上的成功率达到 84.2%。在 SciWorld 上，StraTA 获得了 63.5% 的总分，优于前沿闭源模型。


## 核心贡献

### English
StraTA introduces explicit trajectory-level strategy into agentic reinforcement learning for LLM-based interactive agents. The key insight is that purely reactive agents — which generate each action from the current state alone — couple planning and execution, leading to short-sighted exploration and inconsistent behavior. StraTA decouples these by first sampling a compact natural-language strategy from the initial task state, then conditioning all subsequent actions on this fixed strategy. The framework uses hierarchical GRPO-style training: strategy-level comparisons across different plans, and action-level comparisons across trajectories under the same plan. Three additional techniques enhance learning: top-performing strategy rewards (based on the best fraction of rollouts per strategy), diverse strategy rollout via farthest-point sampling, and critical self-judgment for step-level auxiliary rewards.

### 中文
StraTA 将显式的轨迹级策略引入基于 LLM 的交互式智能体的强化学习中。核心洞察是纯反应式智能体——仅从当前状态生成每个动作——将规划和执行耦合在一起，导致短视探索和不一致行为。StraTA 通过先从初始任务状态采样紧凑的自然语言策略，然后将所有后续动作条件化于此固定策略来解耦两者。该框架使用分级 GRPO 式训练：跨不同计划的策略级比较，以及同一计划下跨轨迹的动作级比较。三种额外技术增强学习：基于每策略最佳 rollout 比例的策略奖励、通过最远点采样的多样化策略 rollout，以及用于步骤级辅助奖励的关键自我判断。

## 方法概述

### English
StraTA formulates long-horizon agentic tasks as finite-horizon MDPs with natural language states and actions. For each task episode: (1) The policy first generates G_s candidate strategies from the initial state. (2) For each strategy, M rollouts are performed, where actions at each step are generated conditioning on both the global strategy and local state. (3) Hierarchical rewards: each strategy receives a reward based on the top-performing fraction (top-ρ) of its rollouts; each action receives the standard trajectory-level reward. (4) Diverse strategy rollout uses farthest-point sampling in embedding space to select semantically distinct strategies from a larger candidate pool. (5) Critical self-judgment: an LLM evaluates whether each action follows the strategy and advances task progress, assigning a step-level penalty when neither condition is met. Training uses a hierarchical GRPO-style objective with strategy-level and action-level clipped surrogate losses.

### 中文
StraTA 将长期智能体任务形式化为有限时域 MDP。每个任务回合：(1) 策略首先生成 G_s 个候选策略。(2) 对每个策略执行 M 次 rollout，每步动作基于全局策略和本地状态共同条件化。(3) 分级奖励：每个策略基于其 rollout 的 top-ρ 部分获得奖励；每个动作获得标准轨迹级奖励。(4) 多样化策略 rollout 在嵌入空间中使用最远点采样，从更大的候选池中选择语义上不同的策略。(5) 关键自我判断：LLM 评估每个动作是否遵循策略并推进任务进展，当两个条件都不满足时分配步骤级惩罚。训练使用分级 GRPO 式目标，包含策略级和动作级裁剪替代损失。

## 实验结果

### English
StraTA was evaluated on ALFWorld, WebShop, and SciWorld benchmarks. Key results: (1) ALFWorld: 1.5B backbone reaches 90.7% success (93.1% with 7B), surpassing GiGPO by up to 4.0%. (2) WebShop: 1.5B backbone reaches 82.5% (84.2% with 7B), surpassing GiGPO by up to 17.5%. (3) SciWorld: 63.5% overall score, outperforming both frontier closed-source models by 6.1% and prior RL baselines by 6.5%, achieving a perfect 100.0% on the Lifespan subset. (4) Strategy guidance consistently improves both sample efficiency and final performance over purely reactive baselines. (5) Diverse strategy rollout and critical self-judgment both provide complementary benefits in ablation studies.

### 中文
StraTA 在 ALFWorld、WebShop 和 SciWorld 基准上评估。关键结果：(1) ALFWorld：1.5B 骨干达 90.7% 成功率（7B 达 93.1%），超过 GiGPO 最多 4.0%。(2) WebShop：1.5B 骨干达 82.5%（7B 达 84.2%），超过 GiGPO 最多 17.5%。(3) SciWorld：63.5% 总分，超过前沿闭源模型 6.1% 和先前 RL 基线 6.5%，在 Lifespan 子集达完美 100.0%。(4) 策略引导持续提升样本效率和最终性能。(5) 消融研究表明多样化策略 rollout 和关键自我判断均提供互补收益。

## 局限性与注意点

### English
(1) Strategy generation quality depends on the base model's planning capability — weaker models may generate poor strategies that hinder rather than help. (2) The hierarchical rollout design increases compute cost (G_s × M rollouts per task). (3) Only tested on text-based interactive environments; applicability to embodied or visual agent tasks is unexplored. (4) The strategy is fixed once generated — adapting strategies mid-episode could further improve performance. (5) The critical self-judgment mechanism adds inference cost per step; cost-performance trade-off not fully characterized. (6) Only GRPO-style training tested; interaction with other RL algorithms (PPO, REINFORCE) not explored.

### 中文
(1) 策略生成质量依赖基座模型的规划能力——较弱模型可能生成差策略，阻碍而非帮助。(2) 分级 rollout 设计增加计算成本（每任务 G_s × M 次 rollout）。(3) 仅在文本交互环境测试；对具身或视觉智能体任务的适用性未探索。(4) 策略一旦生成即固定——回合中期自适应调整策略可能进一步提升性能。(5) 关键自我判断机制每步增加推理成本；成本-性能权衡未充分描述。(6) 仅测试 GRPO 式训练；与其他 RL 算法的交互未探索。

## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [强化学习](../../concepts/reinforcement-learning.html)
- [自动驾驶](../../concepts/autonomous-driving.html)
- [智能体](../../concepts/ai-agents.html)

---
*导入时间: 2026-05-08 06:02*
*来源: arXiv Daily Wiki Update 2026-05-08*
