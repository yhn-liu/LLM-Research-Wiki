---
layout: paper
title: "Stop Holding Your Breath: CT-Informed Gaussian Splatting for Dynamic Bronchoscopy"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28179v1
authors: "Andrea Dunn Beltran, Daniel Rho, Aarav Mehta"
published: 2026-04-30
categories: cs.CV
tags: [cv]
source_url: https://arxiv.org/abs/2604.28179v1
pdf_url: https://arxiv.org/pdf/2604.28179v1
source_type: arxiv_daily
confidence: high
status: analyzed
---

# Stop Holding Your Breath: CT-Informed Gaussian Splatting for Dynamic Bronchoscopy

## 基本信息

- **arXiv ID:** [2604.28179v1](https://arxiv.org/abs/2604.28179v1)
- **作者:** Andrea Dunn Beltran, Daniel Rho, Aarav Mehta et al.
- **发布日期:** 2026-04-30
- **分类:** cs.CV


## 关键图示

<div class="paper-figure-grid">
<figure><img src="../../assets/papers/2604-28179v1/fig1.png" alt="Stop Holding Your Breath: CT-Informed Gaussian Splatting for Dynamic Bronchoscopy Figure 1"><figcaption>Figure 1</figcaption></figure>
<figure><img src="../../assets/papers/2604-28179v1/fig2.png" alt="Stop Holding Your Breath: CT-Informed Gaussian Splatting for Dynamic Bronchoscopy Figure 2"><figcaption>Figure 2</figcaption></figure>
</div>


## 摘要

Bronchoscopic navigation relies on registering endoscopic video to a preoperative CT scan, but respiratory motion deforms the airway by 5-20 mm, creating CT-to-body divergence that limits localization accuracy. In practice, this is mitigated through breath-hold protocols, which attempt to match the intraoperative anatomy to a static CT, but are difficult to reproduce and disrupt clinical workflow. We propose to eliminate the need for breath-hold protocols by leveraging patient-specific respiratory modeling. Paired inhale-exhale CT scans, already acquired for planning, implicitly define the patient-specific deformation space of the breathing airway. By registering these scans, we reduce respiratory motion to a single scalar breathing phase per frame, constraining all reconstructions to anatomically observed configurations. We embed this representation within a mesh-anchored Gaussian splatting framework, where a lightweight estimator infers breathing phase directly from endoscopic RGB, enabling continuous, deformation-aware reconstruction throughout the respiratory cycle without breath-holds or external sensing. To enable quantitative evaluation, we introduce RESPIRE, a physically grounded bronchoscopy simulation pipeline with per-frame ground truth for geometry, pose, breathing phase, and deformation. Experiments on RESPIRE show that our approach achieves geometrically faithful reconstruction, over 20x faster training, and 1.22 mm target localization accuracy (within the 3mm clinically relevant tolerances) outperforming unconstrained single-CT baselines. Please check out our website for additional visuals: https://asdunnbe.github.io/RESPIRE/

## 核心贡献

- **把支气管镜导航中的呼吸运动显式纳入重建。** 论文针对 CT-to-body divergence：术前 CT 是静态的，但术中呼吸会使气道变形 5–20 mm，导致视频到 CT 注册和靶点定位误差。作者主张不再依赖难以复现、打断流程的 breath-hold，而是用患者特异的吸气/呼气 CT 对建模呼吸形变。
- **将复杂气道形变约束为单一 breathing phase。** 通过配准同一患者的 inspiration CT 与 expiration CT，得到共享拓扑 mesh 及位移场；每帧气道状态由 α∈[0,1] 在线性插值表示。这样所有重建都落在真实观察到的解剖轨迹之间，避免 unconstrained deformation 在相机运动和全局气道运动间混淆。
- **提出 CT-informed mesh-anchored Gaussian splatting。** 方法把 3D Gaussian 绑定到 CT-derived airway mesh 的三角面上，用 barycentric coordinate 决定位置、法向对齐方向、薄盘状 primitive 覆盖表面；mesh 随 breathing phase 变形时，Gaussian 自动继承局部平移、旋转和拉伸。
- **设计只从 RGB 估计呼吸相位的优化流程。** 第一帧用深度 grid search 初始化，后续帧仅用 RGB photometric loss 优化 α，并采用带 linear leak 的 cosine 参数化避免 α 接近 0/1 时梯度消失；三阶段优化先调 phase、再调 appearance、最后联合优化，防止外观吸收几何错误。
- **发布/提出 RESPIRE 仿真评估框架。** RESPIRE 从 paired CT 生成带真实呼吸形变、相机位姿、深度、mesh、breathing phase 的支气管镜视频，弥补现有 bronchoscopy 数据集缺乏 deformable ground truth 的问题。

## 方法概述

输入包括术前吸气/呼气 CT、已知相机位姿的单目支气管镜视频，以及由 CT 分割得到的气道 mesh。作者先用 GradICON 对吸气和呼气 mesh 做 deformable registration，得到同拓扑顶点 Vinsp、Vexp 及位移 Δ=Vexp−Vinsp。任意呼吸相位下的 mesh 为 V(α)=Vinsp+αΔ，其中 α=0 表示 full inspiration，α=1 表示 full expiration。

Gaussian 表示继承 BridgeSplat 的 mesh anchoring，但把形变自由度从 per-vertex unconstrained deformation 改成 CT-derived 一维子空间。每个 Gaussian 绑定到 parent triangle，通过 softmax 后的 barycentric coordinate 保证位于三角形内；方向与三角面法向对齐，法向尺度近似为 0，形成贴附气道壁的薄盘。可学习参数主要是 barycentric coordinate、切向尺度和一阶 spherical harmonic 颜色；opacity 初始化后冻结。

呼吸相位估计采用 bounded 参数 θ→α。普通 sigmoid 在 0/1 两端梯度饱和，恰好影响吸/呼极值；作者使用 α=(1−ε)/2·(1−cosθ)+ε·θ/π，ε=0.05，在保持平滑单调的同时提供最小梯度。优化 loss 由 L1+SSIM photometric term 和相邻 α 的 temporal smoothness 组成。由于形变已经由 CT 约束，不需要 BridgeSplat 那类 ARAP、isometric、rigidity、visibility 等额外几何正则。

RESPIRE 评估管线从 COPDGene paired CT 出发，分割气道、注册 mesh，沿 VMTK 提取的 Voronoi airway centerline 生成相机轨迹；呼吸相位按 tidal breathing pressure-volume 曲线模拟，默认 1.5s 吸气、2.5s 呼气；渲染用 Blender Cycles、黏膜 subsurface scattering、湿润高光、空间变化 albedo 和相机同位点光源，输出 RGB、depth、pose、intrinsics、breathing phase 和中间 deformed meshes。

## 实验结果

实验使用 COPDGene 的 9 个病例，每例由 RESPIRE 生成 400+ 帧，覆盖不同气道形态、呼吸幅度、材质和相机路径。对比设置分离两个因素：单 CT vs paired CT deformation，以及 mesh-anchored vs free Gaussians。基线包括 BridgeSplat（单 CT + mesh + unconstrained deformation）、BridgeSplat w/o mesh、Ours w/o mesh 和完整方法。

定量结果显示，完整方法在几何和临床靶点指标上最强：Depth RMSE 为 3.2，δ<1.25 为 0.88；breathing phase MAE 0.158、Pearson r 0.833；contour RMSE 1.24 mm，target error 1.22 mm，低于约 3 mm 的临床相关容差。相比 BridgeSplat 的 depth RMSE 53.8、target error 5.61 mm，说明患者特异 CT 形变显著减少相机运动/气道形变歧义。

渲染质量上，Ours w/o mesh 的 PSNR/SSIM 最高（30.71/0.924），完整方法为 27.37/0.821，仍优于 BridgeSplat mesh 版本（20.65/0.683）。这反映 free Gaussians 可更灵活追求 photometric fit，但缺少 mesh 后无法报告 target/contour 且几何约束较弱；完整方法牺牲部分外观指标换取贴附气道表面的几何忠实性。

效率上，完整方法训练时间 17.4 分钟、1.47 s/frame，相比 BridgeSplat 383.4 分钟、44.24 s/frame 约快 22×。原因是它不再为每帧学习高维 unconstrained deformation，而只优化一个 scalar breathing phase 加较轻量外观参数。

## 局限性与注意点

- 论文明确指出 RESPIRE 依赖准确气道分割，远端或病理区域可能需要人工修正；分割误差会直接影响 deformation field 和重建上限。
- 虽然物理渲染比旧 synthetic bronchoscopy 更真实，仿真到临床视频仍存在 domain gap，可能影响 RGB-only breathing phase 估计的泛化。
- 线性插值 breathing model 只是一阶近似，不能完全表达中间相位的非线性 pressure-volume dynamics 或更复杂局部组织运动。
- 当前假设相机位姿已知；真实临床中若 pose 与 breathing phase 都未知，二者联合估计仍是关键难题。
- 额外 paired inhale/exhale CT 在一些流程中“已有”或“ modest additional acquisition”，但实际临床成本、辐射剂量和协议适配仍需机构级评估。


## 相关概念

- [多模态学习](../../concepts/multimodal-learning.html)
- [强化学习](../../concepts/reinforcement-learning.html)
- [基准评估](../../concepts/benchmarking.html)
- [医学AI](../../concepts/medical-ai.html)

---
*导入时间: 2026-05-02 06:01*
*来源: arXiv Daily Digest 2026-05-02*
