---
layout: paper
title: "PhyCo: Learning Controllable Physical Priors for Generative Motion"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28169v1
authors: "Sriram Narayanan, Ziyu Jiang, Srinivasa Narasimhan"
published: 2026-04-30
categories: cs.CV, cs.AI, cs.LG
tags: [cv, ml, ai]
source_url: https://arxiv.org/abs/2604.28169v1
pdf_url: https://arxiv.org/pdf/2604.28169v1
source_type: arxiv_daily
confidence: high
status: analyzed
---

# PhyCo: Learning Controllable Physical Priors for Generative Motion

## 基本信息

- **arXiv ID:** [2604.28169v1](https://arxiv.org/abs/2604.28169v1)
- **作者:** Sriram Narayanan, Ziyu Jiang, Srinivasa Narasimhan et al.
- **发布日期:** 2026-04-30
- **分类:** cs.CV, cs.AI, cs.LG

## 关键图示

<div class="paper-figure-grid">
<figure><img src="../../assets/papers/2604-28169v1/fig1.jpg" alt="PhyCo: Learning Controllable Physical Priors for Generative Motion Figure 1"><figcaption>Figure 1</figcaption></figure>
<figure><img src="../../assets/papers/2604-28169v1/fig2.jpg" alt="PhyCo: Learning Controllable Physical Priors for Generative Motion Figure 2"><figcaption>Figure 2</figcaption></figure>
<figure><img src="../../assets/papers/2604-28169v1/fig3.png" alt="PhyCo: Learning Controllable Physical Priors for Generative Motion Figure 3"><figcaption>Figure 3</figcaption></figure>
</div>

## 摘要

Modern video diffusion models excel at appearance synthesis but still struggle with physical consistency: objects drift, collisions lack realistic rebound, and material responses seldom match their underlying properties. We present PhyCo, a framework that introduces continuous, interpretable, and physically grounded control into video generation. Our approach integrates three key components: (i) a large-scale dataset of over 100K photorealistic simulation videos where friction, restitution, deformation, and force are systematically varied across diverse scenarios; (ii) physics-supervised fine-tuning of a pretrained diffusion model using a ControlNet conditioned on pixel-aligned physical property maps; and (iii) VLM-guided reward optimization, where a fine-tuned vision-language model evaluates generated videos with targeted physics queries and provides differentiable feedback. This combination enables a generative model to produce physically consistent and controllable outputs through variations in physical attributes-without any simulator or geometry reconstruction at inference. On the Physics-IQ benchmark, PhyCo significantly improves physical realism over strong baselines, and human studies confirm clearer and more faithful control over physical attributes. Our results demonstrate a scalable path toward physically consistent, controllable generative video models that generalize beyond synthetic training environments.

## 核心贡献

- **把“物理属性”做成可连续控制的视频生成条件。** 论文不只是给视频模型加运动提示，而是显式学习摩擦、恢复系数、形变参数、外力大小与方向等物理属性，并用像素对齐的 property map 注入扩散模型，使同一初始帧能随属性变化产生滑动、反弹、变形、受力方向等可解释运动差异。
- **构建 PhyCo 物理仿真数据集。** 作者用 Kubric、PyBullet 和 Blender 生成超过 100K 个照片级仿真视频，覆盖滑块、墙面反弹、垂直弹跳、软球坠落、物体撞击可形变体、多球碰撞等场景，并系统变化外观、材质、相机、HDRI 光照与物理参数；相较 CLEVRER、Physion、Force Prompting 等，强调照片真实、多视角、多物体与物理属性标注。
- **提出两阶段训练管线。** 第一阶段冻结 Cosmos-Predict2-2B 主干，只训练 ControlNet 分支做物理监督微调；第二阶段用经过短程适配的 Qwen2.5-VL-3B 对生成视频回答物理问题，把 yes/no logit 差转成可反传的 VLM reward，从而提高生成结果对输入物理条件的服从度。
- **展示仿真到真实/风格化场景的组合泛化。** 论文重点声称，推理时不需要 3D 重建、材料反演或物理求解器，模型可将简单仿真中学到的物理先验迁移到人物跳弹床、复杂表面滑动、组合属性控制等训练外视觉场景。

## 方法概述

- **数据与条件表示：** 每个训练样本包含初始帧、文本提示、目标视频，以及与物体位置对齐的物理属性图。属性被分组 token 化：摩擦/恢复系数一组，Neo-Hookean 形变参数一组，外力大小与方向 `(cosφ, sinφ)` 一组；每组由独立 ControlNet 分支处理以支持组合性。
- **物理监督微调：** 基础 DiT 视频扩散模型保持冻结，ControlNet 和适配器把属性图编码注入 denoising 过程；训练目标沿用 Cosmos 的 diffusion score-matching loss。这样模型保留预训练视觉生成能力，同时把“同一视觉对象在不同物理参数下应如何运动”的监督集中写入控制分支。
- **VLM 物理反馈：** 作者认为单步 denoising 的模糊中间结果不适合 VLM 评价，因此采用 10 步 rollout 解码完整视频，再用物理问题库询问摩擦是否导致减速、恢复系数是否导致更大反弹、形变是否明显、运动方向是否落入标注扇区等。VLM 对正确/错误答案 token 的 logit 差构成二元交叉熵式 reward loss。
- **训练重点：** 第二阶段只用 VLM loss 更新与物理属性相关的 ControlNet 层，不再混合 score matching；论文报告这种做法比联合训练更稳定，也更直接提升控制 fidelity。

## 实验结果

- **Physics-IQ：** 在 120 帧外推设置下，ControlNet+VLM 版本总体 IQ Score 为 36.3，高于 SVD-XT 19.1、CogVideo-I2V-5B 27.1、Cosmos-Predict2-2B 27.7、VLIPP 34.6；在训练时长条件下生成 57 帧并重复最后一帧时，ControlNet+VLM 达到 43.6，高于文本微调 36.5 和无 VLM 的 ControlNet 38.9。
- **人类偏好：** 16 名参与者进行 2AFC 对比，PhyCo 在物理真实感上相对 Force Prompting 的 force 维度获得 71.7% 偏好；相对 CogVideoX 与 Cosmos，在摩擦、恢复系数、形变、外力等维度多数达到 82%–100% 偏好，说明人类能观察到更可信的属性变化。
- **属性控制消融：** 在 100 个合成测试视频上，VLM 奖励使误差进一步下降：力方向角误差从无 VLM ControlNet 的 38.05° 降到 22.53°，恢复系数误差从 0.28 降到 0.16，形变误差从 0.14 降到 0.10。
- **真实视频力方向：** 对 25 个真实视频施加随机力方向时，PhyCo 平均方向误差 15.2°，Force Prompting 为 40.5°，显示像素对齐属性图比单一 force prompt 更能约束运动方向。
- **定性结果：** 图 1、4、5、6、7 支持论文的主张：模型能在风格化或真实对象中改变弹跳、滑动、形变、受力方向，并能组合 friction+force、restitution+deformation 等属性。

## 局限性与注意点

- **物理覆盖仍偏向可视、低维属性。** 数据集虽大，但场景被作者刻意设计为“物理信号清晰、当前扩散模型能学会”的简洁交互；复杂流体、破碎、布料缠绕、多体长时接触等并未成为主要训练对象。
- **VLM reward 依赖代理判断。** Qwen2.5-VL-3B 只做约 200 步适配，报告约 85% 准确率；其 yes/no 物理问答并不等同于严格物理测量，可能把视觉显著性误判为物理正确。
- **外推时长与真实物理守恒仍有限。** Physics-IQ 的 120 帧评估与 57 帧训练存在时长错配，论文给出重复最后帧的补充结果，但生成模型是否在更长时域保持动量、能量或接触约束并未被系统证明。
- **合成到真实的证据主要是定性和人评。** 论文展示了强泛化案例，但真实世界没有可控 ground-truth 物理参数，因此对真实场景的定量物理正确性仍需更严谨评估。

## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [多模态学习](../../concepts/multimodal-learning.html)
- [强化学习](../../concepts/reinforcement-learning.html)
- [基准评估](../../concepts/benchmarking.html)

---
*导入时间: 2026-05-02 06:01*
*来源: arXiv Daily Digest 2026-05-02*
