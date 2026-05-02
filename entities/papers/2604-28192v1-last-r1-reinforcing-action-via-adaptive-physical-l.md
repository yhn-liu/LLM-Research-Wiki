---
layout: paper
title: "LaST-R1: Reinforcing Action via Adaptive Physical Latent Reasoning for VLA Models"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28192v1
authors: "Hao Chen, Jiaming Liu, Zhonghao Yan"
published: 2026-04-30
categories: cs.RO, cs.CV
tags: [cv]
source_url: https://arxiv.org/abs/2604.28192v1
pdf_url: https://arxiv.org/pdf/2604.28192v1
source_type: arxiv_daily
confidence: high
status: analyzed
---

# LaST-R1: Reinforcing Action via Adaptive Physical Latent Reasoning for VLA Models

## 基本信息

- **arXiv ID:** [2604.28192v1](https://arxiv.org/abs/2604.28192v1)
- **作者:** Hao Chen, Jiaming Liu, Zhonghao Yan et al.
- **发布日期:** 2026-04-30
- **分类:** cs.RO, cs.CV


## 关键图示

<div class="paper-figure-grid">
<figure><img src="../../assets/papers/2604-28192v1/fig1.png" alt="LaST-R1: Reinforcing Action via Adaptive Physical Latent Reasoning for VLA Models Figure 1"><figcaption>Figure 1</figcaption></figure>
<figure><img src="../../assets/papers/2604-28192v1/fig2.png" alt="LaST-R1: Reinforcing Action via Adaptive Physical Latent Reasoning for VLA Models Figure 2"><figcaption>Figure 2</figcaption></figure>
<figure><img src="../../assets/papers/2604-28192v1/fig3.png" alt="LaST-R1: Reinforcing Action via Adaptive Physical Latent Reasoning for VLA Models Figure 3"><figcaption>Figure 3</figcaption></figure>
</div>


## 摘要

Vision-Language-Action (VLA) models have increasingly incorporated reasoning mechanisms for complex robotic manipulation. However, existing approaches share a critical limitation: whether employing explicit linguistic reasoning that suffers from latency and discretization, or utilizing more expressive continuous latent reasoning, they are predominantly confined to static imitation learning that limits adaptability and generalization. While online reinforcement learning (RL) has been introduced to VLAs to enable trial-and-error exploration, current methods exclusively optimize the vanilla action space, bypassing the underlying physical reasoning process. In this paper, we present \textbf{LaST-R1}, a unified VLA framework that integrates latent Chain-of-Thought (CoT) reasoning over physical dynamics prior to action execution, along with a tailored RL post-training paradigm. Specifically, we propose \textbf{Latent-to-Action Policy Optimization (LAPO)}, a novel RL algorithm that jointly optimizes the latent reasoning process and the action generation. By bridging reasoning and control, LAPO improves the representation of physical world modeling and enhances robustness in interactive environments. Furthermore, an \textbf{adaptive latent CoT mechanism} is introduced to allow the policy to dynamically adjust its reasoning horizon based on environment complexity. Extensive experiments show that LaST-R1 achieves a near-perfect 99.8\% average success rate on the LIBERO benchmark with only one-shot supervised warm-up, significantly improving convergence speed and performance over prior state-of-the-art methods. In real-world deployments, LAPO post-training yields up to a 44\% improvement over the initial warm-up policy across four complex tasks, including both single-arm and dual-arm settings. Finally, LaST-R1 demonstrates strong generalization across simulated and real-world environments.

## 核心贡献

- **把 VLA 的“先推理再行动”从离线模仿推进到在线强化学习。** 论文认为现有显式语言 CoT 延迟高且离散化粗糙，连续 latent reasoning 虽更适合控制但多停留在静态 imitation learning；而已有 VLA-RL 通常只优化 action space，忽略产生动作前的物理推理过程。LaST-R1 的主张是：环境奖励应同时塑造 latent reasoning 和 action generation。
- **提出 LaST-R1 架构。** 模型基于 Qwen3-VL-4B/SigLIP2-Large 一类 VLM/VLA backbone，先自回归生成若干 latent CoT token 表示未来物理动态，再条件化并行解码 action token。连续动作被离散化为 token，动作 chunk 覆盖 SE(3) 控制；单臂为 7-DoF，双臂扩展为 14-DoF。
- **用 DINOv3 未来视觉表征锚定 latent reasoning。** 作者不采用简单 pooling、卷积下采样或 Q-Former，而是离线提取未来观测的 DINOv3 CLS embedding，并通过 top-k 选取与 VLA hidden size 对齐的 latent target，使 latent token 更接近全局语义与空间结构先验；训练/推理时不额外运行 DINOv3。
- **提出 LAPO（Latent-to-Action Policy Optimization）。** LAPO 将 latent token 视为隐式决策变量，用 step-level likelihood ratio 同时优化 latent 分布和 action token 分布，并用 GAE 产生的 advantage 将环境成败信号回传到“好推理流形”和动作策略。
- **提出 adaptive latent CoT。** 模型可在多个候选位置发出 `<latent_end>`，根据任务复杂度动态选择 reasoning horizon；训练时采样不同长度探索，推理时以高置信阈值提前结束，从而在复杂任务保留推理能力，在简单反应任务减少延迟。

## 方法概述

LaST-R1 将 VLA policy 定义为从视觉观测和语言指令到 H-step action chunk 的策略。输入图像经视觉编码器得到 dense visual token，与语言 token 一起进入 LLM backbone。不同于直接输出动作，模型先自回归生成 latent reasoning token，用它们表示对未来物理状态和动态的内部预测；随后插入 `<latent_end>`，并复用 KV cache 以并行方式生成 action token，提高控制推理效率。动作 tokenizer 是参数无关的，将连续控制量映射到离散 token，再反解为机器人末端执行器控制。

latent target 的构造是架构关键。论文用 DINOv3 对未来观测提取全局视觉 embedding，按通道幅值 top-k 选取 2560 维作为 latent target，与 Qwen3-VL hidden size 对齐。这样 latent CoT 不只是可学习占位符，而被强视觉基础模型的结构化表征约束，帮助模型在行动前形成物理动态先验。由于这些 target 离线预计算，在线训练和部署不增加 DINOv3 推理成本。

LAPO 的 rollout 阶段记录每步的 latent 序列、action 序列、log-prob、value 和任务奖励。更新时，action 部分使用离散 token 的联合 log probability 构造 PPO 式 clipped ratio；latent 部分把旧策略产生的连续 latent 近似为以当前策略输出为中心的 isotropic Gaussian，基于整段 latent 序列的欧氏距离构造 latent likelihood ratio。总 loss 包含 action policy loss、latent policy loss 和 value loss；adaptive 版本再加入 `<latent_end>` 的 transition loss。

adaptive latent CoT 把停止推理也看作策略决策。作者设定最多 8 个 latent token，并限制 `<latent_end>` 只在 4 个候选位置出现，以避免长度抖动。rollout 时按候选位置 logits 的温度化 categorical 分布采样推理长度，形成探索；推理时若 `<latent_end>` 概率超过 0.99 即停止。优势函数会惩罚复杂场景中过早行动，也会奖励可预测场景中的短推理路径。

## 实验结果

在 LIBERO 四个 suite（Spatial/Object/Goal/Long）上，LaST-R1 使用每任务单条专家轨迹做 SFT warm-up，再进行 online RL。最终平均成功率达到 99.8%，四个 suite 分别为 99.8、100.0、100.0、99.4，排名第一；相比 πRL 的平均 98.3%，长时程 LIBERO-Long 从 94.0 提升到 99.4。论文强调，许多 SFT baseline 使用完整专家数据，而 LaST-R1 只用 one-shot warm-up 后 RL，即可超过 OpenVLA-OFT、π0.5 等强基线。学习曲线显示 LAPO 比 action-only PPO 收敛更快，最终成功率更高。

消融验证了三点：第一，latent reasoning 在 SFT warm-up 后就把平均 SR 从 action-only 的 51.0% 提到 62.0%，LIBERO-Long 从 26.2% 到 48.6%；RL 后完整 LaST-R1+LAPO 达 99.8%，而 Action-Only+PPO 为 94.6%。第二，DINOv3 latent representation 优于卷积、Q-Former、global pooling，RL 后分别对比 99.8%、98.4%、97.2%、96.8%。第三，固定 latent 长度从 1 到 8 token 成功率单调提高但 4 到 8 边际收益变小；adaptive CoT 中 4 个 `<latent_end>` 候选位置效果最好，优于过密候选导致的不稳定。

真实机器人实验包含 Franka 单臂和双臂任务：插入六边形块、拉开袋子拉链、用海绵擦花瓶、打开瓶盖。每任务 30 条演示 warm-up，LoRA 方式进行真实世界 RL，20 次 rollout 评估。原始场景平均成功率从 warm-up 后 52.5% 提升到 RL 后 93.75%，单项可达 90–95%。在 unseen object、background、lighting 三类泛化设置下，RL 后平均性能下降约 8%，明显小于 warm-up policy，说明在线物理反馈增强了鲁棒性和跨条件泛化。

## 局限性与注意点

- 论文未设置独立的 limitations 段，需谨慎看待其结果外推：LIBERO 和四个真实任务虽覆盖较广，但仍集中在桌面操作，尚不能证明对开放世界、长时安全约束或高风险接触任务的可靠性。
- LAPO 需要在线环境交互；在真实机器人上 RL 成本、硬件磨损、安全监控和失败恢复机制没有被充分量化。
- latent ratio 把连续 latent 近似为 isotropic Gaussian，并用固定 σ 调节，这是一种工程化近似；不同 latent 空间尺度或 backbone 下稳定性可能需要重新调参。
- DINOv3 未来表征依赖包含未来观测的数据构造，适合训练阶段监督 latent，但实际部署时 latent 是否总能学到可解释、可验证的物理动态仍需更多诊断。


## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [多模态学习](../../concepts/multimodal-learning.html)
- [强化学习](../../concepts/reinforcement-learning.html)
- [基准评估](../../concepts/benchmarking.html)

---
*导入时间: 2026-05-02 06:01*
*来源: arXiv Daily Digest 2026-05-02*
