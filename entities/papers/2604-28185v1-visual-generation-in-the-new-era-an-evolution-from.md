---
layout: paper
title: "Visual Generation in the New Era: An Evolution from Atomic Mapping to Agentic World Modeling"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28185v1
authors: "Keming Wu, Zuhao Yang, Kaichen Zhang"
published: 2026-04-30
categories: cs.CV
tags: [cv]
source_url: https://arxiv.org/abs/2604.28185v1
pdf_url: https://arxiv.org/pdf/2604.28185v1
source_type: arxiv_daily
confidence: high
status: analyzed
---

# Visual Generation in the New Era: An Evolution from Atomic Mapping to Agentic World Modeling

## 基本信息

- **arXiv ID:** [2604.28185v1](https://arxiv.org/abs/2604.28185v1)
- **作者:** Keming Wu, Zuhao Yang, Kaichen Zhang et al.
- **发布日期:** 2026-04-30
- **分类:** cs.CV


## 关键图示

<div class="paper-figure-grid">
<figure><img src="../../assets/papers/2604-28185v1/fig1.png" alt="Visual Generation in the New Era: An Evolution from Atomic Mapping to Agentic World Modeling Figure 1"><figcaption>Figure 1</figcaption></figure>
<figure><img src="../../assets/papers/2604-28185v1/fig2.png" alt="Visual Generation in the New Era: An Evolution from Atomic Mapping to Agentic World Modeling Figure 2"><figcaption>Figure 2</figcaption></figure>
<figure><img src="../../assets/papers/2604-28185v1/fig3.png" alt="Visual Generation in the New Era: An Evolution from Atomic Mapping to Agentic World Modeling Figure 3"><figcaption>Figure 3</figcaption></figure>
</div>


## 摘要

Recent visual generation models have made major progress in photorealism, typography, instruction following, and interactive editing, yet they still struggle with spatial reasoning, persistent state, long-horizon consistency, and causal understanding. We argue that the field should move beyond appearance synthesis toward intelligent visual generation: plausible visuals grounded in structure, dynamics, domain knowledge, and causal relations. To frame this shift, we introduce a five-level taxonomy: Atomic Generation, Conditional Generation, In-Context Generation, Agentic Generation, and World-Modeling Generation, progressing from passive renderers to interactive, agentic, world-aware generators. We analyze key technical drivers, including flow matching, unified understanding-and-generation models, improved visual representations, post-training, reward modeling, data curation, synthetic data distillation, and sampling acceleration. We further show that current evaluations often overestimate progress by emphasizing perceptual quality while missing structural, temporal, and causal failures. By combining benchmark review, in-the-wild stress tests, and expert-constrained case studies, this roadmap offers a capability-centered lens for understanding, evaluating, and advancing the next generation of intelligent visual generation systems.

## 核心贡献

- **提出以能力而非架构组织视觉生成演进的五级 taxonomy。** 论文将视觉生成从 Atomic Generation、Conditional Generation、In-Context Generation、Agentic Generation 到 World-Modeling Generation 组织成嵌套能力层级：从一次性外观采样，到受结构/参考约束的生成，再到多参考/多条件上下文一致性、planner–render–verify 闭环，最终到可在干预下保持因果/物理一致的世界建模。
- **把图像生成重新定义为“视觉智能”问题。** 作者认为当前领域的瓶颈已不只是 photorealism，而是空间精确性、持久状态、长程一致性、闭环验证和因果 grounding；许多模型看起来已很强，但仍停留在统计相关与视觉 plausibility。
- **系统梳理模型范式与架构收敛。** 论文回顾 GAN、diffusion、flow matching、autoregressive 和 AR+diffusion/flow hybrid 的发展，强调当前前沿越来越趋向“AR 规划语义，diffusion/flow 渲染细节”的混合模式，以及生成与编辑共享 encoder/tokenizer、condition routing、backbone、decoder 的统一架构。
- **把训练、数据、应用和评估串成一条路线图。** 除模型结构外，论文还讨论 VLM relabeling、合成数据蒸馏、continued training、SFT、偏好/奖励建模、采样加速、条件生成、领域适配、图像编辑和具身视觉预测，试图说明视觉生成进步来自系统栈协同，而非单纯模型规模。
- **用 in-the-wild stress tests 论证标准指标高估进展。** 作者通过拼图重组、地铁图拓扑、等距 tile 坐标、浮力/碰撞/机器人抓取、视频重渲染、物理题图像批注等案例展示：当前模型在审美和语义上强，但在精确结构、图级约束、物理因果和功能性动作持续性上仍脆弱。

## 方法概述

这是一篇 roadmap/survey，而非提出单个训练算法。其方法首先是构建能力层级：L1 Atomic Generation 是从噪声或简单条件到图像的一次性映射；L2 Conditional Generation 加入深度、边缘、布局、参考图等显式约束；L3 In-Context Generation 在单次前向中吸收多参考、多条件和累积上下文，要求身份和视觉状态一致；L4 Agentic Generation 把生成放进 plan–render–critique/verify–revise 的闭环；L5 World-Modeling Generation 要求在特定动作或干预下生成因果正确的未来状态。

在模型层面，论文把历史解释为“上一代瓶颈驱动下一代范式”：GAN 展示一步生成但训练不稳；diffusion 以稳定去噪和 web-scale 扩展取代对抗训练但采样慢；flow matching/rectified flow 通过更直的 noise-to-data transport 降低 NFE；autoregressive 图像 token 化有利于与语言/多模态推理统一；hybrid 架构把 AR 的长上下文规划与 diffusion/flow 的高保真渲染结合。

在架构层面，作者强调生成与编辑正在统一：text-to-image、image-to-image、instruction editing 不再需要不同模型，而是同一个 pipeline 接收不同输入条件。典型组件包括 VAE/VQ/SigLIP/CLIP 等 encoder/tokenizer，AdaLN、cross-attention、in-context concatenation 等 condition routing，DiT/MM-DiT/AR transformer 等 backbone，以及 VAE/VQ/pixel decoder。DiT 路线更利于少步蒸馏，AR 路线更适合有限 MDP 式 RL，hybrid 路线试图折中。

评估方法上，论文不是只汇总 FID、CLIP-score 等指标，而是设计/收集高阶能力压力测试。空间维度考察拼图、地铁图、tile map 等离散结构；物理维度考察浮力反事实、驾驶碰撞、机器人抓取、轨迹合成、视频重渲染和材料切削；视觉-文本-逻辑维度考察在图像上 OCR、解题、布局并写回推导。作者把这些案例映射回 L2–L5，作为定位“当前 frontier 到哪里”的定性证据。

## 实验结果

论文的“实验”主要是案例型压力测试，结论具有定性诊断性质。空间结构测试显示，模型能生成看似专业的拼图、地铁图和等距地图，但无法可靠执行刚性几何、图拓扑和精确坐标约束：拼图任务中模型识别出“热气球+蓝天”语义，却用生成先验补洞而非真正匹配边缘；地铁图满足站点数量和部分样式，却违反四线中心换乘、红蓝交叉次数和黄线分支位置；tile map 在视觉上专业，但 F5/G6/D7 等对象出现 off-by-one 或近邻偏移。

物理与因果测试呈现“局部进步 + 功能性缺口”。在橙片下沉、汽车碰撞、杯子抓取、勺子入碗和蔬菜切削中，模型能生成气泡、折射、车体破碎、抓取姿态、容器遮挡和物体内部纹理等合理视觉后果，显示出一定 world-modeling 萌芽。但视频重渲染中，把厨房人类替换成 humanoid 后，虽然身份一致，却丢失了原序列中的倒液动作及其流体后果，暴露出像素级一致性与功能因果持续性之间的差距。

视觉-文本-逻辑测试中，物理考试图像批注案例显示模型能完成 OCR、图示 grounding、推导、排版和中文公式写回，最终数值链条也自洽；但 reasoning trace 反映其反复重算、修正假设，缺少稳定符号工作区。作者据此提出“VLM-first, renderer-second”解释：模型可能先在隐式/文本空间求解，再通过文档编辑式渲染写回图像；生成能力已足以作为结构化输出界面，但上游推理仍是脆弱瓶颈。

总体发现是：标准 perceptual/CLIP 类 benchmark 会高估能力，因为它们奖励逼真和语义相似，却不充分检查结构、状态、验证和因果。当前前沿模型在 L1/L2 很强，部分 L3/L4 能力正在出现，L5 世界建模仍远未可靠。

## 局限性与注意点

- 论文自身声明是 preprint/evolving roadmap， taxonomy、引用和观点可能随领域更新而修订；其结论应视为路线图和分析框架，而非最终定论。
- 大量 stress tests 是专家设计的定性案例，不是大样本、可重复、统计显著的 benchmark；它们适合暴露 failure mode，但不应直接转化为总体成功率。
- 部分闭源系统的架构和推理流程只能从行为和公开报告推断，关于“AR 规划、diffusion 渲染”或“VLM-first, renderer-second”的机制解释并非全部有白盒证据。
- 论文覆盖范围很广，难免牺牲对单个子领域的细粒度比较；读者应把它当作能力地图，再结合专门 benchmark/论文判断具体模型。


## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [多模态学习](../../concepts/multimodal-learning.html)
- [强化学习](../../concepts/reinforcement-learning.html)
- [基准评估](../../concepts/benchmarking.html)

---
*导入时间: 2026-05-02 06:01*
*来源: arXiv Daily Digest 2026-05-02*
