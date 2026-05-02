---
layout: paper
---
---
layout: paper
title: "Representation Fréchet Loss for Visual Generation"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28190v1
authors: "Jiawei Yang, Zhengyang Geng, Xuan Ju"
published: 2026-04-30
categories: cs.CV
tags: [cv]
source_url: https://arxiv.org/abs/2604.28190v1
pdf_url: https://arxiv.org/pdf/2604.28190v1
source_type: arxiv_daily
confidence: high
status: analyzed
---

# Representation Fréchet Loss for Visual Generation

## 基本信息

- **arXiv ID:** [2604.28190v1](https://arxiv.org/abs/2604.28190v1)
- **作者:** Jiawei Yang, Zhengyang Geng, Xuan Ju et al.
- **发布日期:** 2026-04-30
- **分类:** cs.CV

## 摘要

We show that Fréchet Distance (FD), long considered impractical as a training objective, can in fact be effectively optimized in the representation space. Our idea is simple: decouple the population size for FD estimation (e.g., 50k) from the batch size for gradient computation (e.g., 1024). We term this approach FD-loss. Optimizing FD-loss reveals several surprising findings. First, post-training a base generator with FD-loss in different representation spaces consistently improves visual quality. Under the Inception feature space, a one-step generator achieves0.72 FID on ImageNet 256x256. Second, the same FD-loss repurposes multi-step generators into strong one-step generators without teacher distillation, adversarial training or per-sample targets. Third, FID can misrank visual quality: modern representations can yield better samples despite worse Inception FID. This motivates FDr$^k$, a multi-representation metric. We hope this work will encourage further exploration of distributional distances in diverse representation spaces as both training objectives and evaluation metrics for generative models.

## 核心贡献

- We show that Fréchet Distance (FD), long considered impractical as a training objective, can in fact be effectively optimized in the representation space

## 方法概述

FD-loss.  Optimizing FD-loss reveals several surprising findings.  First, post-training a base generator with FD-loss in different representation spaces consistently improves visual quality.

## 实验结果

that Fréchet Distance (FD)

## 相关论文

<!-- 待填充：添加相关论文链接 -->


## 分析信息

- **分析来源:** summary_extract
- **分析置信度:** medium
- **分析时间:** 2026-05-02 06:02
- **关键词:** AI, ML


## 分析信息

- **分析来源:** pdf_analysis
- **分析置信度:** high
- **分析时间:** 2026-05-02 06:02
- **关键词:** AI, ML
- **PDF 路径:** /root/wiki/raw/papers/2604-28190v1.pdf

---
*导入时间: 2026-05-02 06:01*
*来源: arXiv Daily Digest 2026-05-02*
