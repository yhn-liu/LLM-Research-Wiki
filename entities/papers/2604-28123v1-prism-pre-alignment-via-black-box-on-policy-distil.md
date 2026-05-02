---
layout: paper
---
---
layout: paper
title: "PRISM: Pre-alignment via Black-box On-policy Distillation for Multimodal Reinforcement Learning"
created: 2026-05-01
updated: 2026-05-01
type: paper
arxiv_id: 2604.28123v1
authors: "Sudong Wang, Weiquan Huang, Xiaomin Yu et al. (12 authors)"
published: 2026-04-30
categories: cs.CV, cs.AI, cs.CL
tags: [nlp, cv, ai]
source_url: https://arxiv.org/abs/2604.28123v1
pdf_url: https://arxiv.org/pdf/2604.28123v1
confidence: high
status: analyzed
---

# PRISM: Pre-alignment via Black-box On-policy Distillation for Multimodal Reinforcement Learning

## 基本信息

- **arXiv ID:** [2604.28123v1](https://arxiv.org/abs/2604.28123v1)
- **作者:** Sudong Wang, Weiquan Huang, Xiaomin Yu et al. (12 authors)
- **发布日期:** 2026-04-30
- **分类:** cs.CV, cs.AI, cs.CL

## 摘要

### English

The standard post-training recipe for large multimodal models (LMMs) applies supervised fine-tuning (SFT) on curated demonstrations followed by reinforcement learning with verifiable rewards (RLVR). However, SFT introduces distributional drift that neither preserves the model's original capabilities nor faithfully matches the supervision distribution. This problem is further amplified in multimodal reasoning, where perception errors and reasoning failures follow distinct drift patterns that compound during subsequent RL. We introduce PRISM, a three-stage pipeline that mitigates this drift by inserting an explicit distribution alignment stage between SFT and RLVR. Based on on-policy distillation (OPD) principles, PRISM frames the alignment between the policy and an ensemble-of-experts (MoE) discriminator with specialized perception and reasoning experts as a black-box, response-level adversarial game, providing disentangled correction signals that steer the policy toward the supervision distribution without requiring access to teacher logits. While the 1.26M public demonstrations suffice for broad SFT initialization, distribution alignment demands higher-fidelity supervision; therefore, we curate 113K additional demonstrations from Gemini 3 Flash with dense visual grounding and step-by-step reasoning on the hardest-to-solve problems. Experiments on Qwen3-VL show that PRISM consistently improves downstream RLVR performance across multiple RL algorithms (GRPO, DAPO, GSPO) and multimodal benchmarks.

### 中文

大型多模态模型 (LMM) 的标准训练后配方对策划的演示应用监督微调 (SFT)，然后进行具有可验证奖励的强化学习 (RLVR)。然而，SFT 引入了分布漂移，既不保留模型的原始功能，也不忠实地匹配监督分布。这个问题在多模态推理中被进一步放大，其中感知错误和推理失败遵循不同的漂移模式，并在随后的强化学习过程中复合。我们引入了 PRISM，这是一种三级管道，通过在 SFT 和 RLVR 之间插入显式分布对齐阶段来减轻这种漂移。基于策略蒸馏 (OPD) 原理，PRISM 将策略与具有专门感知和推理专家的专家混合 (MoE) 判别器之间的一致性视为黑盒、响应级对抗游戏，提供解开的纠正信号，引导策略走向监督分布，而无需访问教师逻辑。虽然 126 万次公开演示足以进行广泛的 SFT 初始化，但分布对齐需要更高保真度的监督；因此，我们策划了来自 Gemini 3 Flash 的 113,000 个额外演示，具有密集的视觉基础和对最难解决的问题的逐步推理。Qwen3-VL 上的实验表明，PRISM 在多种 RL 算法（GRPO、DAPO、GSPO）和多种多模态基准测试中持续改进了下游 RLVR 性能。

## 核心贡献

- **发现 SFT 分布漂移问题**：揭示了 SFT 阶段引入的分布漂移在多模态推理中被放大——感知错误和推理失败遵循不同漂移模式，在 RL 阶段复合
- **提出三阶段训练管道 PRISM**：在标准 SFT→RLVR 流程中插入显式分布对齐阶段，形成 SFT→对齐→RLVR 的三阶段架构
- **黑盒在线策略蒸馏**：基于 OPD 原理，将分布对齐建模为黑盒响应级对抗博弈，无需访问教师 logits，利用 MoE 判别器提供感知和推理两个维度的解耦纠正信号
- **高质量数据策划**：策划 11.3 万条来自 Gemini 3 Flash 的额外演示，包含密集视觉标注和逐步推理，用于最难问题
- **跨算法泛化**：在 GRPO、DAPO、GSPO 等多种 RL 算法和多种多模态基准上验证了 PRISM 的一致性改进

## 方法概述

PRISM 的核心思想是在 SFT 和 RLVR 之间插入一个分布对齐阶段。标准的 SFT→RLVR 流程中，SFT 会导致策略分布偏离预训练分布，而多模态场景中感知错误和推理错误的漂移模式不同，直接进入 RL 会复合放大这些问题。

对齐阶段基于在线策略蒸馏 (OPD) 框架，将策略与一个 MoE 判别器之间的交互建模为黑盒对抗博弈。判别器包含专门的感知专家和推理专家，从不同维度评估策略输出与目标分布的一致性，提供解耦的纠正信号。这种方法不需要访问教师模型的 logits，只需响应级别的交互即可工作。

为支撑对齐阶段，作者从 Gemini 3 Flash 策划了 11.3 万条高保真演示，这些演示包含密集的视觉基础标注和逐步推理过程，聚焦于最难的问题。最终在 Qwen3-VL 上验证了 PRISM 在 GRPO、DAPO、GSPO 等多种 RL 算法下的持续性能提升。

## 实验结果

- **基准模型**: Qwen3-VL，多种多模态基准测试
- **RL 算法兼容性**: 在 GRPO、DAPO、GSPO 三种 RL 算法上均获得性能提升
- **数据规模**: 126 万公开演示用于 SFT，11.3 万 Gemini 3 Flash 演示用于分布对齐
- **关键发现**: 分布对齐阶段有效减轻了 SFT 引入的分布漂移，提升了下游 RLVR 的整体表现

## 相关概念

- [强化学习](../../concepts/reinforcement-learning.html)
- [强化学习可验证奖励](../../concepts/rlvr.html)
- [监督微调](../../concepts/supervised-fine-tuning.html)
- [专家混合模型](../../concepts/mixture-of-experts.html)
- [知识蒸馏](../../concepts/knowledge-distillation.html)
- [多模态模型](../../concepts/multimodal-models.html)

---

*导入时间: 2026-05-01 19:53*
*来源: arXiv Daily Digest 2026-05-01*
