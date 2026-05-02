---
layout: paper
title: "Computing Equilibrium beyond Unilateral Deviation"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28186v1
authors: "Mingyang Liu, Gabriele Farina, Asuman Ozdaglar"
published: 2026-04-30
categories: cs.GT, cs.AI, cs.CC
tags: [ml, ai]
source_url: https://arxiv.org/abs/2604.28186v1
pdf_url: https://arxiv.org/pdf/2604.28186v1
source_type: arxiv_daily
confidence: high
status: analyzed
---

# Computing Equilibrium beyond Unilateral Deviation

## 基本信息

- **arXiv ID:** [2604.28186v1](https://arxiv.org/abs/2604.28186v1)
- **作者:** Mingyang Liu, Gabriele Farina, Asuman Ozdaglar
- **发布日期:** 2026-04-30
- **分类:** cs.GT, cs.AI, cs.CC
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2604.28186v1)

## 关键图示

<div class="paper-figure-grid">
<figure><img src="../../assets/papers/2604-28186v1/fig1.png" alt="Computing Equilibrium beyond Unilateral Deviation Figure 1"><figcaption>Figure 1</figcaption></figure>
<figure><img src="../../assets/papers/2604-28186v1/fig2.png" alt="Computing Equilibrium beyond Unilateral Deviation Figure 2"><figcaption>Figure 2</figcaption></figure>
<figure><img src="../../assets/papers/2604-28186v1/fig3.png" alt="Computing Equilibrium beyond Unilateral Deviation Figure 3"><figcaption>Figure 3</figcaption></figure>
</div>

## 摘要

Most familiar equilibrium concepts, such as Nash and correlated equilibrium, guarantee only that no single player can improve their utility by deviating unilaterally. They offer no guarantees against profitable coordinated deviations by coalitions. Although the literature proposes solution concepts that provide stability against multilateral deviations (\emph{e.g.}, strong Nash and coalition-proof equilibrium), these generally fail to exist. In this paper, we study an alternative solution concept that minimizes coalitional deviation incentives, rather than requiring them to vanish, and is therefore guaranteed to exist. Specifically, we focus on minimizing the average gain of a deviating coalition, and extend the framework to weighted-average and maximum-within-coalition gains. In contrast, the minimum-gain analogue is shown to be computationally intractable. For the average-gain and maximum-gain objectives, we prove a lower bound on the complexity of computing such an equilibrium and present an algorithm that matches this bound. Finally, we use our framework to solve the \emph{Exploitability Welfare Frontier} (EWF), the maximum attainable social welfare subject to a given exploitability (the maximum gain over all unilateral deviations).

## 核心贡献

- 提出 **Minimum Average-Strong Equilibrium（MASE）**：不再要求强 Nash、coalition-proof 等多方偏离稳定性“完全存在”，而是在相关联合策略空间中最小化任意联盟可通过联合偏离获得的最大平均收益。
- 给出复杂度刻画：即使只考虑单人联盟，近似计算 MASE 也是 NP-hard；在给定 Utility Dependency Graph 的树分解时，SETH 下计算复杂度必须对该图 treewidth 呈指数依赖。
- 给出与下界匹配的算法：把问题转化为 correlator 与 deviator 的零和元博弈，用 FTPL 避免显式维护指数大的分布，并用基于树分解的动态规划实现线性优化 oracle，使运行时间指数项只依赖 treewidth 而非玩家数。
- 说明框架可扩展到 weighted average/sum 和 coalition 内最大收益目标，同时证明“最小成员收益”版本的 Minimum Strong CCE 即使在小博弈中也难以近似。
- 将框架用于 **Exploitability Welfare Frontier（EWF）**：在给定单边 exploitability 容忍度下计算最大社会福利，从而把“近似可剥削性”与“福利”之间的权衡可计算化。

## 方法概述

- **效用依赖图：** 论文定义 Utility Dependency Graph：若存在某个玩家 k，其效用同时受玩家 i、j 的动作影响，则 i、j 连边。该图不同于常规 graphical game 图，重点刻画联合偏离带来的交互结构；treewidth 被证明是计算 MASE 的关键参数。
- **MASE 目标：** 在相关联合策略 `π ∈ ΔA` 上，最小化 `max_S max_âS (1/|S|) Σ_{i∈S} E[Ui(âS, a−S) − Ui(a)]`。若该值≤0，则可视为无联盟具备正的总平均偏离收益；但 MASE 允许值为正，从而保证总有最优解。
- **元博弈视角：** correlator 选择原博弈的相关联合策略，deviator 选择联盟及其联合偏离；收益为联盟平均偏离收益。由于目标双线性，极点解对应纯联合动作或纯偏离，因此可用在线学习迭代地生成少量纯策略，再取平均。
- **FTPL + 动态规划：** 直接用 LP 或标准 no-regret 会遇到指数动作空间。论文用 Follow the Perturbed Leader，每一步只需求解带随机扰动的线性优化；该优化通过 Utility Dependency Graph 的树分解动态规划求解。
- **收敛与复杂度：** 定理 7.4 给出有限时间的 high-probability 近似 MASE 保证；设扰动参数 η≈1/√T 时误差随 1/√T 缩小，总运行时间形如 `O(T · |S| · |T| · A^{tw(G)+1})`，与树宽下界的指数依赖相匹配。
- **EWF 计算：** 对 exploitability 与社会福利构造带权目标，把单人联盟和全体联盟放入同一 MASE 式框架；调节权重 w 可走 Pareto frontier，并可通过二分搜索满足目标 exploitability 的最大福利点。

## 实验结果

- **经典博弈验证：** 在囚徒困境中，MASE 对应以 0.5 概率选择 (C,D) 与 (D,C)，社会福利为 1.0；而 NE/CCE 及多种 no-regret baseline 收敛到 (D,D)，社会福利仅 0.4。该例表明 MASE 在控制联盟偏离风险的同时可选出更高福利的相关策略。
- **Stag Hunt 中的均衡选择：** baseline 倾向收敛到福利较差的均衡，而 MASE 收敛到更好的均衡；同时其单边 exploitability 与 baseline 接近，但对多方 coalition exploitability 更稳健。
- **与 Optimal CCE 比较：** 论文将 MASE、baseline、LP 真值和“coalition exploitability 最小的 CCE”对比，显示 Optimal CCE 与 MASE 在联盟可剥削性上接近，而 FTRL、Hedge、FTPL、OMD 等标准算法明显更脆弱。
- **更大随机博弈：** 在随机 normal-form games 中，随着玩家数或动作数增长，baseline 的 coalition exploitability 上升；在随机 polymatrix games 中，即使只考虑大小不超过 2 的联盟，标准 no-regret 平均策略也随规模和交互度增长而更易被 coalition 偏离利用。
- **EWF 结构：** 论文证明并展示 EWFCCE 随 exploitability 非递减、凹、分段线性；在囚徒困境、Stag Hunt、Chicken、Pigou 网络等示例中画出不同的福利—可剥削性曲线。

## 局限性与注意点

- 理论上已证明一般 succinct games 中计算困难；算法适用的可扩展性依赖 Utility Dependency Graph 的 treewidth 较小，以及能获得或构造有效树分解。
- 实验主要是小型经典博弈、随机 normal-form/polymatrix 示例，用于验证算法和概念差异；尚不是大规模真实多智能体系统中的工程评测。
- MASE 优化的是联盟平均收益，隐含 transferable-utility 或“联盟内收益可再分配”的解释；若应用场景要求每个成员都受益、最弱成员收益或其他公平目标，结论和可计算性会不同，论文也指出 minimum-gain 版本更难。
- 该框架采用相关联合策略；如果实际系统不能实现相关装置或集中协调，MASE 解的可执行性需要额外机制支持。

## 相关概念

- [强化学习](../../concepts/reinforcement-learning.html)
- [医学AI](../../concepts/medical-ai.html)
- [图神经网络](../../concepts/graph-neural-networks.html)
- [智能体](../../concepts/ai-agents.html)

---
*导入时间: 2026-05-02 06:01*
*来源: arXiv Daily Digest 2026-05-02*
