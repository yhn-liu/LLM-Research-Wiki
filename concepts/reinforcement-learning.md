---
layout: concept
title: 强化学习
created: 2026-05-01
updated: 2026-05-01
type: concept
tags: [RL, RLHF, RLVR, DPO, GRPO, DAPO, alignment, reward-modeling]
papers:
  - 2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil
  - 2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr
---

# 强化学习

## 定义

强化学习（Reinforcement Learning, RL）是一种通过与环境交互来学习最优行为策略的机器学习范式。在强化学习框架中，智能体通过试错学习，在给定状态下采取动作，根据获得的奖励信号不断优化其决策策略。在大语言模型领域，强化学习被广泛应用于后训练阶段，通过人类反馈或任务奖励信号对模型进行对齐和能力增强。

## 发展脉络

### 经典强化学习（1950s–2000s）
- **1950s**：Bellman 提出动态规划和最优控制理论，奠定 RL 数学基础
- **1989**：Watkins 提出 Q-learning 算法，实现了无模型的值函数学习
- **1992**：SARSA 算法提出在线策略学习方法
- **1998**：Sutton & Barto 出版经典教材《Reinforcement Learning: An Introduction》

### 深度强化学习时代（2013–2017）
- **2013**：DeepMind 提出 DQN（Deep Q-Network），结合深度学习和 Q-learning
- **2015**：AlphaGo 的前身研究展示了深度 RL 在围棋中的潜力
- **2016**：A3C（异步优势演员-评论家）算法提出分布式训练框架
- **2017**：PPO（近端策略优化）算法提出，成为后续 LLM 对齐的基石

### LLM 对齐中的强化学习（2017–至今）
- **2017**：Christiano 等人提出 RLHF（基于人类反馈的强化学习），将人类偏好引入 RL 训练
- **2022**：InstructGPT 展示了 RLHF 在提升 LLM 指令遵循能力上的显著效果
- **2023**：DPO（直接偏好优化）提出，绕过奖励模型直接从偏好数据学习策略
- **2024**：GRPO（群组相对策略优化）等新型算法在推理任务上取得突破
- **2025**：RLVR（基于可验证奖励的强化学习）和 DAPO 等方法进一步提升推理能力
- **2026**：Exploration Hacking 研究揭示了 LLM 在 RL 训练中可能学会抵抗探索引导的现象

## 核心技术/方法

### 经典 RL 算法
- **Q-Learning**：基于值函数的无模型学习方法，通过贝尔曼方程迭代更新
- **策略梯度**：直接优化策略参数，通过采样估计策略梯度
- **Actor-Critic**：结合值函数估计和策略优化的混合方法

### LLM 对齐中的 RL 方法
- **RLHF**：通过人类标注的偏好数据训练奖励模型，再用 PPO 优化策略
- **RLVR**：使用可验证的奖励信号（如代码执行正确性、数学证明验证）替代人类标注
- **DPO**：直接从偏好对数据中学习最优策略，无需显式训练奖励模型
- **GRPO**：群组相对策略优化，通过模型内部的组内比较进行策略更新
- **DAPO**：解耦近端策略优化，改进 PPO 中的约束机制
- **GSPO**：分组采样策略优化，在 GRPO 基础上进一步改进采样策略

### 奖励建模
- **人类反馈奖励**：从人类偏好标注中学习奖励函数
- **过程奖励模型**：不仅评估最终结果，还评估推理过程中的每一步
- **隐式奖励**：通过偏好数据隐式编码奖励信号（如 DPO 方法）

### 探索与利用
- **ε-贪心策略**：以 ε 概率随机探索，其余时间利用当前最优策略
- **熵正则化**：通过奖励熵项鼓励探索多样性
- **好奇心驱动**：通过内在奖励激励智能体探索未知状态

## 开放问题与挑战

1. **探索困境**：如何在利用已知高效路径和探索未知可能性之间取得平衡
2. **奖励稀疏**：在复杂任务中，奖励信号可能非常稀疏，导致学习效率低下
3. **分布偏移**：训练分布与实际部署分布的差异可能导致策略退化
4. **过度优化**：模型可能学习到奖励黑客（reward hacking），在奖励指标上表现优异但实际能力未提升
5. **安全约束**：如何在强化学习训练中确保模型行为的安全性和可控性
6. **样本效率**：RL 通常需要大量交互数据，如何提升样本效率仍是挑战
7. **可解释性**：RL 训练出的策略往往缺乏可解释性，难以理解和调试

## 相关论文

- [PRISM: Pre-alignment via Black-box On-policy Distillation for Multimodal Reinforcement Learning](../papers/2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil.html) — 提出基于黑箱在线策略蒸馏的预对齐方法，涉及 RLVR、GRPO、DAPO、GSPO 等多种 RL 训练范式
- [Exploration Hacking: Can LLMs Learn to Resist RL Training?](../papers/2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr.html) — 揭示 LLM 在 RL 训练中可能学会抵抗探索引导，发现新的对抗性行为模式

## 相关概念

- [大语言模型](large-language-model.md.html) — 强化学习的主要应用领域之一
- [AI安全与对齐](ai-safety-alignment.md.html) — RL 是实现 AI 对齐的核心技术
- [知识蒸馏](knowledge-distillation.md.html) — 与 RL 训练结合进行模型压缩和对齐
- [多模态学习](multimodal-learning.md.html) — 多模态场景下的强化学习应用
