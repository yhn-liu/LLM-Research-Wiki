---
layout: paper
title: "Generalizable Sparse-View 3D Reconstruction from Unconstrained Images"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28193v1
authors: "Vinayak Gupta, Chih-Hao Lin, Shenlong Wang"
published: 2026-04-30
categories: cs.CV
tags: [cv]
source_url: https://arxiv.org/abs/2604.28193v1
pdf_url: https://arxiv.org/pdf/2604.28193v1
source_type: arxiv_daily
confidence: high
status: analyzed
---

# Generalizable Sparse-View 3D Reconstruction from Unconstrained Images

## 基本信息

- **arXiv ID:** [2604.28193v1](https://arxiv.org/abs/2604.28193v1)
- **作者:** Vinayak Gupta, Chih-Hao Lin, Shenlong Wang et al.
- **发布日期:** 2026-04-30
- **分类:** cs.CV
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2604.28193v1)

## 关键图示

<div class="paper-figure-grid">
<figure><img src="../../assets/papers/2604-28193v1/fig1.png" alt="Generalizable Sparse-View 3D Reconstruction from Unconstrained Images Figure 1"><figcaption>Figure 1</figcaption></figure>
<figure><img src="../../assets/papers/2604-28193v1/fig2.png" alt="Generalizable Sparse-View 3D Reconstruction from Unconstrained Images Figure 2"><figcaption>Figure 2</figcaption></figure>
<figure><img src="../../assets/papers/2604-28193v1/fig3.png" alt="Generalizable Sparse-View 3D Reconstruction from Unconstrained Images Figure 3"><figcaption>Figure 3</figcaption></figure>
</div>

## 摘要

Reconstructing 3D scenes from sparse, unposed images remains challenging under real-world conditions with varying illumination and transient occlusions. Existing methods rely on scene-specific optimization using appearance embeddings or dynamic masks, which requires extensive per-scene training and fails under sparse views. Moreover, evaluations on limited scenes raise questions about generalization. We present GenWildSplat, a feed-forward framework for sparse-view outdoor reconstruction that requires no per-scene optimization. Given unposed internet images, GenWildSplat predicts depth, camera parameters, and 3D Gaussians in a canonical space using learned geometric priors. An appearance adapter modulates appearance for target lighting conditions, while semantic segmentation handles transient objects. Through curriculum learning on synthetic and real data, GenWildSplat generalizes across diverse illumination and occlusion patterns. Evaluations on PhotoTourism and MegaScenes benchmark demonstrate state-of-the-art feed-forward rendering quality, achieving real-time inference without test-time optimization

## 核心贡献

- 提出 **GenWildSplat**：面向稀疏、无位姿、互联网式户外图像集合的前馈 3D Gaussian Splatting 重建框架，2–6 张输入、约 3 秒完成推理，不需要每个场景的测试时优化。
- 将 in-the-wild 重建中的三个难点统一处理：稀疏视角、光照/外观变化、行人车辆等 transient occluders；相比传统 NeRF/3DGS 方法，不依赖密集视图和长时间 per-scene optimization。
- 在 AnySplat/VGGT 几何先验基础上加入 **appearance adapter**，把 canonical Gaussian colors 按目标 light code 调制到对应光照，使外观控制发生在 3D 表示中而不是逐图 2D 风格迁移。
- 用外部语义分割先验生成 transient mask，避免模型把人、车等动态物体错误解释为静态几何；同时通过课程学习将光照、跨场景泛化和遮挡建模分阶段训练，稳定这个高度欠定问题。
- 构建更具挑战的 MegaScenes 稀疏视角评测，并在 PhotoTourism 与 MegaScenes 上相对优化式和前馈式 baseline 取得更好的实时重建质量。

## 方法概述

- **基础架构：** GenWildSplat 继承 AnySplat 的 feed-forward 结构，用 VGGT transformer 从无位姿多视角图像中提取几何/语义特征，三个 head 分别预测深度、相机内外参和 per-pixel Gaussian 参数（尺度、旋转、不透明度、颜色等），再反投影到 canonical 3D Gaussians。
- **外观建模：** Light Encoder 从每张图提取 16 维 light code；MLP 将其扩展并调制 Gaussian 的球谐颜色系数。这样同一 canonical geometry 可在不同目标光照下渲染，支持 cross-scene illumination transfer。
- **遮挡处理：** 使用 YOLOv8 segmentation 检测 person、car、bus、truck 等 transient 类别，生成二值 mask；训练损失只在静态区域计算 MSE + λ perceptual loss，避免内生 visibility map 在无监督训练中塌缩。
- **课程学习：** Stage 1 在单一合成场景的光照变化上学习几何—外观解耦；Stage 2 引入多个合成场景学习泛化先验；Stage 3 加入合成 transient occlusions 和 mask 监督，学习遮挡处理。论文称直接在真实大规模数据上联合学习几何、光照、遮挡会不稳定。
- **训练细节：** 24 层 transformer，DPT-style heads，初始化自 AnySplat；在 700+ DL3DV 户外场景上训练，使用 DiffusionRenderer 离线生成光照变化、COCO segmentation 合成遮挡；40K iterations（10K/10K/20K），单张 RTX A6000 约 2 天。

## 实验结果

- **PhotoTourism：** 在 6 输入视角的稀疏设定中，优化式 in-the-wild 方法即便用 VGGT 位姿替换 COLMAP 以增强 baseline，仍容易在稀疏视角下产生几何尖刺、模糊和外观不一致；GenWildSplat 无需场景特定训练即可产生更真实的渲染。
- **MegaScenes 定量：** 3-view 下 GS-W/WildGaussians/NexusSplats 的 PSNR 分别为 11.60/12.73/13.17，GenWildSplat 为 14.43；6-view 下三者为 12.01/13.29/13.92，GenWildSplat 达 15.84，并且推理时间为 3 秒，而 baseline 需 2.4–8 小时。
- **前馈 baseline：** Vanilla AnySplat、2D StyleTransfer+AnySplat、DiffusionRenderer+AnySplat 在 MegaScenes 上分别为 PSNR 12.65/12.90/13.59，SSIM 0.311/0.281/0.309；GenWildSplat 为 PSNR 15.84、SSIM 0.440、LPIPS 0.407，并保持 view-consistent。
- **消融：** 去掉 appearance adapter 后无法处理外观变化（PSNR 13.76、SSIM 0.391）；去掉 occlusion handling 后 LPIPS 恶化到 0.513；去掉 curriculum 后颜色/训练塌缩明显（PSNR 11.72）；完整模型为 PSNR 15.84、SSIM 0.440。
- **外观迁移：** 论文展示跨场景光照转移，说明模型将 appearance 与 geometry 部分解耦，能用另一场景的目标光照渲染当前场景，而传统 jointly optimized appearance embedding 难以直接做到。

## 局限性与注意点

- 稀疏输入天然无法覆盖所有区域，未观测区域会出现缺失几何；当测试视角远离训练/输入视角分布时，可能产生伪影或双层几何。
- 论文主要面向户外 in-the-wild 场景；室内场景中遮挡 mask 若不能准确捕捉物体或深度不连续，重建质量会下降。
- 方法不建模投影阴影，也不支持物理一致的真实 relighting；appearance adapter 更接近外观调制，而不是完整光传输模拟。
- 训练依赖合成光照、合成遮挡、预训练分割和 AnySplat/VGGT 先验；这些模块的偏差会影响最终泛化。
- 文中 SyncFix 后处理只用于可视化、不纳入 baseline 比较；阅读 qualitative 图时需要注意哪些展示经过后处理。

## 相关概念

- [三维重建](../../concepts/3d-reconstruction.html)
- [高斯泼溅](../../concepts/gaussian-splatting.html)
- [新视角合成](../../concepts/novel-view-synthesis.html)
- [稀疏视角重建](../../concepts/sparse-view-reconstruction.html)
- [计算机视觉](../../concepts/computer-vision.html)

---
*导入时间: 2026-05-02 06:01*
*来源: arXiv Daily Digest 2026-05-02*
