---
layout: paper
---
---
layout: paper
title: "Defending Quantum Classifiers against Adversarial Perturbations through Quantum Autoencoders"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28176v1
authors: "Emma Andrews, Sahan Sanjaya, Prabhat Mishra"
published: 2026-04-30
categories: quant-ph, cs.LG
tags: [ml]
source_url: https://arxiv.org/abs/2604.28176v1
pdf_url: https://arxiv.org/pdf/2604.28176v1
source_type: arxiv_daily
confidence: medium
status: partial
key_figures: [assets/papers/2604-28176v1/fig1.png, assets/papers/2604-28176v1/fig2.png, assets/papers/2604-28176v1/fig3.png]
---

# Defending Quantum Classifiers against Adversarial Perturbations through Quantum Autoencoders

## 基本信息

- **arXiv ID:** [2604.28176v1](https://arxiv.org/abs/2604.28176v1)
- **作者:** Emma Andrews, Sahan Sanjaya, Prabhat Mishra
- **发布日期:** 2026-04-30
- **分类:** quant-ph, cs.LG
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2604.28176v1)

## 今日导读

- **相关主题:** 多模态学习 / 基准评估 / AI安全与对齐
- **方法信号:** In this paper, we propose an adversarial training-free defense framework that utilizes a quantum autoencoder to purify the adversarial samples through reconstruction.
- **阅读优先级:** 中：最新 arXiv 方向论文

## 关键图示

<div class="paper-figure-grid">
<figure><img src="../../assets/papers/2604-28176v1/fig1.png" alt="Defending Quantum Classifiers against Adversarial Perturbations through Quantum Autoencoders Figure 1"><figcaption>Figure 1</figcaption></figure>
<figure><img src="../../assets/papers/2604-28176v1/fig2.png" alt="Defending Quantum Classifiers against Adversarial Perturbations through Quantum Autoencoders Figure 2"><figcaption>Figure 2</figcaption></figure>
<figure><img src="../../assets/papers/2604-28176v1/fig3.png" alt="Defending Quantum Classifiers against Adversarial Perturbations through Quantum Autoencoders Figure 3"><figcaption>Figure 3</figcaption></figure>
</div>

## 摘要

Machine learning models can learn from data samples to carry out various tasks efficiently. When data samples are adversarially manipulated, such as by insertion of carefully crafted noise, it can cause the model to make mistakes. Quantum machine learning models are also vulnerable to such adversarial attacks, especially in image classification using variational quantum classifiers. While there are promising defenses against these adversarial perturbations, such as training with adversarial samples, they face practical limitations. For example, they are not applicable in scenarios where training with adversarial samples is either not possible or can overfit the models on one type of attack. In this paper, we propose an adversarial training-free defense framework that utilizes a quantum autoencoder to purify the adversarial samples through reconstruction. Moreover, our defense framework provides a confidence metric to identify potentially adversarial samples that cannot be purified the quantum autoencoder. Extensive evaluation demonstrates that our defense framework can significantly outperform state-of-the-art in prediction accuracy (up to 68%) under adversarial attacks.

## 核心贡献（摘要级初筛）

- In this paper, we propose an adversarial training-free defense framework that utilizes a quantum autoencoder to purify the adversarial samples through reconstruction.
- Moreover, our defense framework provides a confidence metric to identify potentially adversarial samples that cannot be purified the quantum autoencoder.
- Extensive evaluation demonstrates that our defense framework can significantly outperform state-of-the-art in prediction accuracy (up to 68%) under adversarial attacks.

## 方法概述（摘要级初筛）

In this paper, we propose an adversarial training-free defense framework that utilizes a quantum autoencoder to purify the adversarial samples through reconstruction.

> 注：本页不再依赖 PDF 译文生成；以上为根据 arXiv 元数据和摘要即时生成的快速导读。后续可在阅读全文后升级为 `status: analyzed`。

## 实验结果

Extensive evaluation demonstrates that our defense framework can significantly outperform state-of-the-art in prediction accuracy (up to 68%) under adversarial attacks.

## 相关概念

- [多模态学习](../../concepts/multimodal-learning.html)
- [基准评估](../../concepts/benchmarking.html)
- [AI安全与对齐](../../concepts/ai-safety-alignment.html)

---
*导入时间: 2026-05-02 16:44*
*来源: arXiv Daily Wiki Update 2026-05-02*
