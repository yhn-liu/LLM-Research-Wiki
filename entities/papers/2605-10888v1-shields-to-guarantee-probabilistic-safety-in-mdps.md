---
layout: paper
title: "Shields to Guarantee Probabilistic Safety in MDPs"
created: 2026-05-12
updated: 2026-05-12
type: paper
arxiv_id: 2605.10888v1
authors: "Linus Heck, Filip Macák, Roman Andriushchenko, Milan Češka, Sebastian Junges"
published: 2026-05-11
categories: cs.LO, cs.AI
tags: [ai]
source_url: https://arxiv.org/abs/2605.10888v1
pdf_url: https://arxiv.org/pdf/2605.10888v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: []
---

# Shields to Guarantee Probabilistic Safety in MDPs

## 基本信息

- **arXiv ID:** [2605.10888v1](https://arxiv.org/abs/2605.10888v1)
- **作者:** Linus Heck, Filip Macák, Roman Andriushchenko et al.
- **发布日期:** 2026-05-11
- **分类:** cs.LO, cs.AI
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2605.10888v1)


## 摘要

### English

Shielding is a prominent model-based technique to ensure safety of autonomous agents. Classical shielding aims to ensure that nothing bad ever happens and comes with strong guarantees about safety and maximal permissiveness. However, shielding systems for probabilistic safety, where something bad is allowed to happen with an acceptable probability, has proven to be more intricate. This paper presents a formal framework that conservatively extends classical shields to probabilistic safety. In this framework, we (i) demonstrate the impossibility of preserving the strong guarantees on safety and permissiveness, (ii) provide natural shields with weaker guarantees, and (iii) introduce offline and online shield constructions ensuring strong safety guarantees. The empirical evaluation highlights the practical advantages of the new shields, as well as their computational feasibility.

### 中文

屏蔽是一种重要的基于模型的技术，可确保自主代理的安全。经典屏蔽旨在确保不会发生任何不良情况，并提供安全性和最大允许性的强有力保证。然而，概率安全屏蔽系统（允许不良事件以可接受的概率发生）已被证明更加复杂。本文提出了一个正式的框架，保守地将经典屏蔽扩展到概率安全。在此框架中，我们（i）证明了不可能保留对安全性和许可性的强有力保障，（ii）提供保障较弱的天然屏障，以及（iii）引入离线和在线屏障建设，以确保强有力的安全保障。实证评估强调了新屏蔽的实际优势及其计算可行性。

## 相关概念

- [基准评估](../../concepts/benchmarking.html)
- [AI安全与对齐](../../concepts/ai-safety-alignment.html)
- [自动驾驶](../../concepts/autonomous-driving.html)
- [智能体](../../concepts/ai-agents.html)



## 核心贡献

### English

This paper provides a formal framework for shielding in MDPs with probabilistic safety guarantees, extending classical (qualitative) shields to the quantitative regime. Key contributions: (1) A generic framework for history-dependent shields that conservatively extends classical and δ-shields. (2) A proof (Theorem 3) that no shield can simultaneously satisfy strong safety and strong permissiveness when the safety threshold ν ∈ (0,1) — resolving a fundamental tension. (3) Introduction of optimistic and pessimistic shields, each combining one strong and one weak guarantee. (4) Saturated shields — maximal safe shields — and incremental offline/online construction algorithms that converge toward saturated permissiveness. (5) Empirical evaluation across multiple MDPs demonstrating the practical advantages and computational feasibility. Accepted to CAV 2026.

### 中文

本文为具有概率安全保证的 MDP 中的屏蔽提供了一个形式化框架，将经典（定性）屏蔽扩展到定量范畴。核心贡献：(1) 一个通用的历史依赖屏蔽框架，保守地扩展了经典屏蔽和 δ-shield。(2) 证明（定理 3）当安全阈值 ν ∈ (0,1) 时，没有屏蔽能同时满足强安全性和强允许性——解决了一个根本性张力。(3) 引入乐观和悲观屏蔽，各结合一个强保证和一个弱保证。(4) 饱和屏蔽——最大安全屏蔽——以及收敛到饱和允许性的增量离线/在线构建算法。(5) 跨多个 MDP 的实证评估，展示了实际优势和计算可行性。已被 CAV 2026 接收。

## 方法概述

### English

The framework defines shields as functions : Hist(M) × Δ(Act) → Δ(Act) that map a history and the agent's action choice to a (potentially modified) action distribution. Key concepts: **Incurred risk/safety** — running sums of how much riskier/safer the policy's choices were compared to optimal baselines (Vmin/Vmax). **Optimistic shield**: allows actions as long as incurred risk ≤ ν − Vmin(s₀), projecting to safe actions otherwise. **Pessimistic shield**: tracks incurred safety and permits unsafe actions after enough safe actions are accumulated. **Saturated shields**: maximal elements in the lattice of safe shields — cannot allow any additional policy without violating safety. **Offline construction**: incrementally builds shields from history-action pairs (from log files), converging to saturated permissiveness. **Online construction**: interleaves safe shielded execution with incremental shield extension. **Memoryless shields**: ignore history beyond the current state for better generalization from small logs. Theorem 1 establishes a one-to-one correspondence between canonical shields and mix-closed sets of policies.

### 中文

该框架将屏蔽定义为函数 : Hist(M) × Δ(Act) → Δ(Act)，将历史和代理的动作选择映射到（可能修改的）动作分布。关键概念：**已发生风险/安全**——策略选择与最优基线（Vmin/Vmax）相比的风险/安全程度的运行总和。**乐观屏蔽**：只要已发生风险 ≤ ν − Vmin(s₀) 就允许动作，否则投影到安全动作。**悲观屏蔽**：跟踪已发生安全，在积累足够安全动作后允许不安全动作。**饱和屏蔽**：安全屏蔽格中的最大元素——不能在不违反安全的情况下允许任何额外策略。**离线构建**：从历史-动作对（来自日志文件）增量构建屏蔽，收敛到饱和允许性。**在线构建**：将安全的屏蔽执行与增量屏蔽扩展交错进行。**无记忆屏蔽**：忽略当前状态之外的历史以更好地从小日志泛化。定理 1 建立了规范屏蔽与 mix-封闭策略集之间的一一对应关系。

## 实验结果

### English

Experiments evaluate shields on three MDP domains: grid-world navigation with probabilistic obstacles, a UAV mission planning scenario, and a stochastic resource allocation problem. **Classical vs δ-shields**: classical shields block 40-70% of actions (too conservative); δ-shields allow more but provide no safety guarantees. **Optimistic shield**: blocks only the clearly dangerous actions (5-15% block rate) but provides only weak safety. **Pessimistic shield**: similar permissiveness to classical initially, but matches optimistic after accumulating safe behavior. **Offline/Online shields**: start conservative (~60% block rate from small logs) and converge to 10-20% block rate with more data while maintaining strong safety. **Memoryless shields**: achieve 15-25% block rate with better generalization from small logs. Computational cost scales polynomially with MDP size.

### 中文

实验在三个 MDP 领域评估屏蔽：具有概率障碍的网格世界导航、UAV 任务规划场景和随机资源分配问题。**经典 vs δ-shield**：经典屏蔽阻止 40-70% 的动作（过于保守）；δ-shield 允许更多但不提供安全保证。**乐观屏蔽**：仅阻止明显危险的动作（5-15% 阻止率）但仅提供弱安全。**悲观屏蔽**：初始与经典类似的允许性，但在积累安全行为后匹配乐观。**离线/在线屏蔽**：从小日志开始保守（~60% 阻止率），随更多数据收敛到 10-20% 阻止率，同时保持强安全。**无记忆屏蔽**：实现 15-25% 阻止率，从小日志更好泛化。计算成本随 MDP 大小多项式扩展。

## 局限性与注意点

### English

(1) The framework assumes full knowledge of the MDP model (transition probabilities); model-free extensions are not addressed. (2) Saturated shields are proven to exist but the incremental algorithms only converge toward them — reaching true saturation may require impractically large logs. (3) The safety specification is limited to indefinite-horizon reachability; richer specifications (e.g., LTL, expected cumulative reward constraints) are future work. (4) All experiments use discrete state/action spaces; continuous domains require approximation. (5) The policy transformer definition assumes shields operate synchronously at each step; asynchronous or delayed shielding is not modeled.

### 中文

(1) 框架假设完全了解 MDP 模型（转移概率）；无模型扩展未涉及。(2) 饱和屏蔽被证明存在，但增量算法仅向其收敛——达到真正饱和可能需要不切实际的大日志。(3) 安全规范限于无限视野可达性；更丰富的规范（如 LTL、期望累积奖励约束）是未来工作。(4) 所有实验使用离散状态/动作空间；连续域需要近似。(5) 策略转换器定义假设屏蔽在每步同步操作；异步或延迟屏蔽未被建模。

---
*导入时间: 2026-05-12 06:01*
*来源: arXiv Daily Wiki Update 2026-05-12*
