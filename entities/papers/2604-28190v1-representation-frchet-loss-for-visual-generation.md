---
layout: paper
title: "Representation Fréchet Loss for Visual Generation"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28190v1
authors: "Jiawei Yang, Zhengyang Geng, Xuan Ju, Yonglong Tian, Yue Wang"
published: 2026-04-30
categories: cs.CV
tags: [cv]
source_url: https://arxiv.org/abs/2604.28190v1
pdf_url: https://arxiv.org/pdf/2604.28190v1
source_type: arxiv_daily
confidence: medium
status: needs_pdf_lm_analysis
key_figures: [assets/papers/2604-28190v1/fig1.jpg, assets/papers/2604-28190v1/fig2.png, assets/papers/2604-28190v1/fig3.jpg]
---

# Representation Fréchet Loss for Visual Generation

## 基本信息

- **arXiv ID:** [2604.28190v1](https://arxiv.org/abs/2604.28190v1)
- **作者:** Jiawei Yang, Zhengyang Geng, Xuan Ju et al.
- **发布日期:** 2026-04-30
- **分类:** cs.CV
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2604.28190v1)

## 摘要

We show that Fréchet Distance (FD), long considered impractical as a training objective, can in fact be effectively optimized in the representation space. Our idea is simple: decouple the population size for FD estimation (e.g., 50k) from the batch size for gradient computation (e.g., 1024). We term this approach FD-loss. Optimizing FD-loss reveals several surprising findings. First, post-training a base generator with FD-loss in different representation spaces consistently improves visual quality. Under the Inception feature space, a one-step generator achieves0.72 FID on ImageNet 256x256. Second, the same FD-loss repurposes multi-step generators into strong one-step generators without teacher distillation, adversarial training or per-sample targets. Third, FID can misrank visual quality: modern representations can yield better samples despite worse Inception FID. This motivates FDr$^k$, a multi-representation metric. We hope this work will encourage further exploration of distributional distances in diverse representation spaces as both training objectives and evaluation metrics for generative models.

## 深度解读状态

> 待 PDF 下载并由 LM 阅读后补充。本文详情页不会使用 arXiv 元数据或摘要快速导读冒充完整解读。

## 相关概念

- [多模态学习](../../concepts/multimodal-learning.html)
- [基准评估](../../concepts/benchmarking.html)
- [AI安全与对齐](../../concepts/ai-safety-alignment.html)
- [医学AI](../../concepts/medical-ai.html)

---
*导入时间: 2026-05-02 16:38*
*来源: arXiv Daily Wiki Update 2026-05-02*
