---
layout: paper
title: "PRISM: Pre-alignment via Black-box On-policy Distillation for Multimodal Reinforcement Learning"
arxiv_id: 2604.28123v1
authors: ""
published: 2026-05-01
categories: cs.CV, cs.AI, cs.CL
tags: [nlp, cv, ai]
type: paper
source_url: https://arxiv.org/abs/2604.28123v1
pdf_url: https://arxiv.org/pdf/2604.28123v1
---


# PRISM: Pre-alignment via Black-box On-policy Distillation for Multimodal Reinforcement Learning

## 基本信息

- **arXiv ID:** [2604.28123v1](https://arxiv.org/abs/2604.28123v1)
- **作者:** Sudong Wang, Weiquan Huang, Xiaomin Yu et al. (12 authors)
- **发布日期:** 2026-04-30
- **分类:** cs.CV, cs.AI, cs.CL

## 摘要

### English

The standard post-training recipe for large multimodal models (LMMs) applies supervised fine-tuning (SFT) on curated demonstrations followed by reinforcement learning with verifiable rewards (RLVR). However, SFT introduces distributional drift that neither preserves the model's original capabilities nor faithfully matches the supervision distribution. This problem is further amplified in multimodal reasoning, where perception errors and reasoning failures follow distinct drift patterns that comp

### 中文

大型多模态模型 (LMM) 的标准训练后配方对策划的演示应用监督微调 (SFT)，然后进行具有可验证奖励的强化学习 (RLVR)。然而，SFT 引入了分布漂移，既不保留模型的原始功能，也不忠实地匹配监督分布。这个问题在多模态推理中被进一步放大，其中感知错误和推理失败遵循不同的漂移模式，并在随后的强化学习过程中复合。我们引入了 PRISM，这是一种三级管道，通过在 SFT 和 RLVR 之间插入显式分布对齐阶段来减轻这种漂移。基于策略蒸馏 (OPD) 原理，PRISM 将策略与具有专门感知和推理专家的专家混合 (MoE) 判别器之间的一致性视为黑盒、响应级对抗游戏，提供解开的纠正信号，引导策略走向监督分布，而无需访问教师逻辑。虽然 126 万次公开演示足以进行广泛的 SFT 初始化，但分布对齐需要更高保真度的监督；因此，我们策划了来自 Gemini 3 Flash 的 113,000 个额外演示，具有密集的视觉基础和对最难解决的问题的逐步推理。 Qwen3-VL 上的实验表明，PRISM 在多种 RL 算法（GRPO、DAPO、GSPO）和多种多模态基准测试中持续改进了下游 RLVR 性

## 核心贡献

- ### English

The standard post-training recipe for large multimodal models (LMMs) applies supervised fine-tuning (SFT) on curated demonstrations followed by reinforcement learning with verifiable rewards (RLVR)

## 方法概述

s optimize it by reweighting or regularizing next-token likelihood (Qin & Springenberg, 2025; Zhu et al. , 2025).  * Equal contribution.

## 实验结果

that PRISM consistently improves downstream RLVR performance across multiple RL algorithms (GRPO

## 相关论文

<!-- 待填充：添加相关论文链接 -->


## 分析信息

- **分析来源:** summary_extract
- **分析置信度:** medium
- **分析时间:** 2026-05-01 20:14
- **关键词:** reinforcement learning, RL, fine-tuning, multimodal, vision


## 分析信息

- **分析来源:** pdf_analysis
- **分析置信度:** high
- **分析时间:** 2026-05-01 20:20
- **关键词:** LLM, large language model, reinforcement learning, RL, fine-tuning, multimodal, vision
- **PDF 路径:** /root/wiki/raw/papers/2604-28123v1.pdf

---
*导入时间: 2026-05-01 19:53*
*来源: arXiv Daily Digest 2026-05-01*
