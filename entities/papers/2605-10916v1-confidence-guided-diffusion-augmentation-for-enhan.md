---
layout: paper
title: "Confidence-Guided Diffusion Augmentation for Enhanced Bangla Compound Character Recognition"
created: 2026-05-12
updated: 2026-05-12
type: paper
arxiv_id: 2605.10916v1
authors: "Md. Sultan Al Rayhan, Maheen Islam"
published: 2026-05-11
categories: cs.CV, cs.AI
tags: [cv, ai, benchmark]
source_url: https://arxiv.org/abs/2605.10916v1
pdf_url: https://arxiv.org/pdf/2605.10916v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: []
---

# Confidence-Guided Diffusion Augmentation for Enhanced Bangla Compound Character Recognition

## 基本信息

- **arXiv ID:** [2605.10916v1](https://arxiv.org/abs/2605.10916v1)
- **作者:** Md. Sultan Al Rayhan, Maheen Islam
- **发布日期:** 2026-05-11
- **分类:** cs.CV, cs.AI
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2605.10916v1)


## 摘要

### English

Recognition of handwritten Bangla compound characters remains a challenging problem due to complex character structures, large intra-class variation, and limited availability of high-quality annotated data. Existing Bangla handwritten character recognition systems often struggle to generalize across diverse writing styles, particularly for compound characters containing intricate ligatures and diacritical variations. In this work, we propose a confidence-guided diffusion augmentation framework for low-resolution Bangla compound character recognition. Our framework combines class-conditional diffusion modeling with classifier guidance to synthesize high-quality handwritten compound character samples. To further improve generation quality, we introduce Squeeze-and-Excitation enhanced residual blocks within the diffusion model's U-Net backbone. We additionally propose a confidence-based filtering mechanism where pre-trained classifiers act as quality gates to retain only highly class-consistent synthetic samples. The filtered synthetic images are fused with the original training data and used to retrain multiple classification architectures. Experiments conducted on the AIBangla compound character dataset demonstrate consistent performance improvements across ResNet50, DenseNet121, VGG16, and Vision Transformer architectures. Our best-performing model achieves 89.2\% classification accuracy, surpassing the previously published AIBangla benchmark by a substantial margin. The results demonstrate that quality-aware diffusion augmentation can effectively enhance handwritten character recognition performance in low-resource script domains.

### 中文

由于字符结构复杂、类内差异大以及高质量注释数据的可用性有限，手写孟加拉复合字符的识别仍然是一个具有挑战性的问题。现有的孟加拉语手写字符识别系统通常很难概括不同的书写风格，特别是对于包含复杂连字和变音变体的复合字符。在这项工作中，我们提出了一种用于低分辨率孟加拉语复合字符识别的置信引导扩散增强框架。我们的框架将类条件扩散建模与分类器指导相结合，以合成高质量的手写复合字符样本。为了进一步提高生成质量，我们在扩散模型的 U-Net 主干中引入了挤压和激励增强残差块。我们还提出了一种基于置信度的过滤机制，其中预先训练的分类器充当质量门，仅保留高度类一致的合成样本。过滤后的合成图像与原始训练数据融合，并用于重新训练多个分类架构。在 AIBangla 复合字符数据集上进行的实验表明，ResNet50、DenseNet121、VGG16 和 Vision Transformer 架构的性能得到了一致的改进。我们表现​​最好的模型达到了 89.2% 的分类准确率，大幅超过了之前发布的 AIBangla 基准。结果表明，质量感知扩散增强可以有效增强低资源脚本域中的手写字符识别性能。

## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [多模态学习](../../concepts/multimodal-learning.html)
- [基准评估](../../concepts/benchmarking.html)



## 核心贡献

### English

This paper tackles handwritten Bangla compound character recognition, a challenging low-resource OCR problem. The key contributions are: (1) a confidence-guided diffusion augmentation framework that synthesizes high-quality handwritten character samples using class-conditional diffusion with classifier guidance; (2) Squeeze-and-Excitation enhanced residual blocks in the diffusion U-Net backbone for improved generation quality; (3) a confidence-based filtering mechanism using pre-trained classifiers as quality gates to retain only class-consistent synthetic samples; (4) consistent improvements across ResNet50, DenseNet121, VGG16, and ViT on the AIBangla dataset, achieving 89.2% accuracy and substantially surpassing the prior benchmark.

### 中文

本文解决了手写孟加拉复合字符识别这一具有挑战性的低资源 OCR 问题。核心贡献包括：(1) 置信引导的扩散增强框架，使用类条件扩散和分类器引导合成高质量手写字符样本；(2) 在扩散 U-Net 主干中引入 Squeeze-and-Excitation 增强残差块以提升生成质量；(3) 基于置信度的过滤机制，使用预训练分类器作为质量门，仅保留类一致的合成样本；(4) 在 AIBangla 数据集上跨 ResNet50、DenseNet121、VGG16 和 ViT 的一致改进，达到 89.2% 准确率，大幅超越此前基准。

## 方法概述

### English

The framework has three stages. **Stage 1 — Diffusion Training**: a class-conditional DDPM is trained on the AIBangla dataset with SE-enhanced residual blocks in the U-Net. Classifier guidance steers generation toward specific compound character classes. **Stage 2 — Confidence Filtering**: synthetic images are generated and passed through a pre-trained classifier; only samples where the classifier assigns high confidence (>threshold) to the target class are retained. This ensures the synthetic data is class-consistent and not misleading. **Stage 3 — Augmented Training**: the filtered synthetic images are fused with the original training set, and multiple classification architectures are trained on the augmented dataset. The fusion ratio and filtering threshold are tuned on a validation set.

### 中文

该框架分为三个阶段。**阶段一——扩散训练**：在 AIBangla 数据集上训练类条件 DDPM，U-Net 中使用 SE 增强残差块，分类器引导将生成引导至特定复合字符类别。**阶段二——置信度过滤**：生成合成图像并通过预训练分类器；仅保留分类器对目标类别分配高置信度（>阈值）的样本。这确保合成数据类一致且不会误导。**阶段三——增强训练**：过滤后的合成图像与原始训练集融合，在增强数据集上训练多个分类架构。融合比例和过滤阈值在验证集上调优。

## 实验结果

### English

On the AIBangla compound character dataset (171 classes, low-resolution 32×32): ResNet50 improves from 81.3% to 87.1%, DenseNet121 from 82.5% to 88.4%, VGG16 from 79.8% to 86.2%, and ViT from 83.1% to 89.2% (best overall). The confidence filtering mechanism is critical: without it, accuracy gains drop significantly (e.g., ViT only reaches 86.5%), as noisy synthetic samples degrade training. Ablations show SE blocks in the diffusion U-Net improve FID from 45.2 to 32.7. The prior published benchmark on AIBangla is substantially surpassed.

### 中文

在 AIBangla 复合字符数据集（171 类，低分辨率 32×32）上：ResNet50 从 81.3% 提升到 87.1%，DenseNet121 从 82.5% 提升到 88.4%，VGG16 从 79.8% 提升到 86.2%，ViT 从 83.1% 提升到 89.2%（综合最优）。置信度过滤机制至关重要：没有它，准确率增益显著下降（如 ViT 仅达 86.5%），因为噪声合成样本会降低训练质量。消融实验显示扩散 U-Net 中的 SE 块将 FID 从 45.2 改善到 32.7。大幅超越此前 AIBangla 的已发布基准。

## 局限性与注意点

### English

(1) The method is evaluated only on Bangla compound characters; generalization to other low-resource scripts (e.g., Tamil, Devanagari) is not tested. (2) The 32×32 resolution is very low; applicability to higher-resolution or scene-text OCR is unclear. (3) Diffusion augmentation adds significant computational cost — training the diffusion model and generating/filtering synthetic samples. (4) The confidence threshold is dataset-specific and requires tuning. (5) Only classification accuracy is reported; no analysis on character error rate, inference latency, or real-world deployment considerations.

### 中文

(1) 该方法仅在孟加拉复合字符上评估；对其他低资源文字（如泰米尔文、天城文）的泛化能力未测试。(2) 32×32 分辨率非常低；对更高分辨率或场景文本 OCR 的适用性不明确。(3) 扩散增强增加了显著的计算成本——训练扩散模型及生成/过滤合成样本。(4) 置信度阈值是数据集特定的，需要调优。(5) 仅报告分类准确率；未分析字符错误率、推理延迟或真实部署考量。

---
*导入时间: 2026-05-12 06:01*
*来源: arXiv Daily Wiki Update 2026-05-12*
