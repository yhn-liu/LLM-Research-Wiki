---
layout: paper
title: "Feature-Augmented Transformers for Robust AI-Text Detection Across Domains and Generators"
created: 2026-05-06
updated: 2026-05-06
type: paper
arxiv_id: 2605.03969v1
authors: "Mohamed Mady, Johannes Reschke, Björn Schuller"
published: 2026-05-05
categories: cs.CL, cs.AI
tags: [nlp, ai, benchmark]
source_url: https://arxiv.org/abs/2605.03969v1
pdf_url: https://arxiv.org/pdf/2605.03969v1
source_type: arxiv_daily
confidence: medium
status: analyzed
confidence: high
key_figures: []
---

# Feature-Augmented Transformers for Robust AI-Text Detection Across Domains and Generators

## 基本信息

- **arXiv ID:** [2605.03969v1](https://arxiv.org/abs/2605.03969v1)
- **作者:** Mohamed Mady, Johannes Reschke, Björn Schuller
- **发布日期:** 2026-05-05
- **分类:** cs.CL, cs.AI
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2605.03969v1)


## 摘要

### English

AI-generated text is nowadays produced at scale across domains and heterogeneous generation pipelines, making robustness to distribution shift a central requirement for supervised binary detectors. We train transformer-based detectors on HC3 PLUS and calibrate a single decision threshold by maximising balanced accuracy on held-out validation; this threshold is then kept fixed for all downstream test distributions, revealing domain- and generator-dependent error asymmetries under shift. We evaluate in-domain on HC3 PLUS, under cross-dataset transfer to the multi-domain, multi-generator M4 benchmark, and on the external AI-Text-Detection-Pile. Although base models achieve near-ceiling in-domain performance (up to 99.5% balanced accuracy), performance under shift is brittle and strongly model-dependent. Feature augmentation via attention-based linguistic feature fusion improves transfer, with our best model (DeBERTa-v3-base+FeatAttn) achieving 85.9% balanced accuracy on M4. Multi-seed experiments confirm high stability. Under the same fixed-threshold protocol, our model outperforms strong zero-shot baselines by up to +7.22 points. Category-level ablations further show that readability and vocabulary features contribute most to robustness under shift. Overall, these results demonstrate that feature augmentation and a modern DeBERTa backbone significantly outperform earlier BERT/RoBERTa models, while the fixed-threshold protocol provides a more realistic and informative assessment of practical detector robustness.

### 中文

如今，人工智能生成的文本是跨领域和异构生成管道大规模生成的，这使得分布式转变的鲁棒性成为监督二进制检测器的核心要求。我们在 HC3 PLUS 上训练基于变压器的检测器，并通过最大化保留验证的平衡精度来校准单个决策阈值；然后，对于所有下游测试分布，该阈值保持固定，从而揭示偏移下与域和生成器相关的误差不对称性。我们在 HC3 PLUS 上进行域内评估，在跨数据集传输到多域、多生成器 M4 基准测试的情况下，以及在外部 AI-Text-Detection-Pile 上进行评估。尽管基础模型实现了接近上限的域内性能（高达 99.5% 的平衡精度），但移位下的性能很脆弱并且强烈依赖于模型。通过基于注意力的语言特征融合进行特征增强可改善迁移，我们的最佳模型 (DeBERTa-v3-base+FeatAttn) 在 M4 上实现了 85.9% 的平衡准确率。多种子实验证实了高稳定性。在相同的固定阈值协议下，我们的模型比强大的零样本基线高出 7.22 个点。类别级别的消融进一步表明，可读性和词汇特征对转变下的稳健性贡献最大。总体而言，这些结果表明，特征增强和现代 DeBERTa 主干明显优于早期的 BERT/RoBERTa 模型，而固定阈值协议提供了对实际检测器鲁棒性的更现实和信息丰富的评估。

## 核心贡献

### English

This paper demonstrates that supervised AI-text detectors, despite near-ceiling in-domain performance (99.5% balanced accuracy on HC3 PLUS), are brittle under distribution shift when evaluated with a deployment-realistic fixed-threshold protocol. The key methodological contribution is the fixed-threshold evaluation: a single decision threshold is calibrated once on held-out validation data and kept fixed across all downstream test distributions, revealing domain- and generator-dependent error asymmetries. Feature augmentation via an attention-based linguistic feature fusion module substantially improves cross-domain transfer, with DeBERTa-v3-base+FeatAttn achieving 85.9% balanced accuracy on the multi-domain, multi-generator M4 benchmark.

### 中文

本文证明监督式 AI 文本检测器尽管在域内性能接近天花板（HC3 PLUS 上 99.5% 平衡准确率），但在使用部署现实固定阈值协议评估时，在分布偏移下表现脆弱。关键方法论贡献是固定阈值评估：单次在校验集上校准决策阈值并在所有下游测试分布中保持固定，揭示了依赖域和生成器的错误不对称性。通过基于注意力的语言特征融合模块进行特征增强显著改善了跨域迁移，DeBERTa-v3-base+FeatAttn 在多域多生成器 M4 基准上达到 85.9% 平衡准确率。

## 方法概述

### English

Detectors are trained on HC3 PLUS (human-written vs ChatGPT answers with semantic-invariant rewrites) and evaluated under three protocols: (1) in-domain on HC3 PLUS, (2) cross-dataset transfer to M4 (English: 78,766 samples across Wikipedia, WikiHow, Reddit, arXiv, PeerRead domains and 8 generator families), and (3) external testing on AI-Text-Detection-Pile. Feature-augmented variants fuse 62 handcrafted linguistic features (lexical diversity, POS/stylometric, readability, punctuation, LM-based perplexity/burstiness) with transformer [CLS] representations via a learnable attention module. The top-30 features are selected once on training data via mutual information and point-biserial correlation ranking.

### 中文

检测器在 HC3 PLUS（人类与 ChatGPT 回答及语义不变改写）上训练，在三种协议下评估：(1) HC3 PLUS 域内；(2) 跨数据集迁移至 M4（英语：78,766 样本，覆盖 Wikipedia、WikiHow、Reddit、arXiv、PeerRead 和 8 个生成器家族）；(3) AI-Text-Detection-Pile 外部测试。特征增强变体通过可学习注意力模块将 62 个手工语言特征（词汇多样性、POS/文体、可读性、标点、基于 LM 的困惑度/突发性）与 transformer [CLS] 表示融合。通过互信息和点双列相关排序在训练数据上一次性选出前 30 个特征。

## 实验结果

### English

Base models achieve up to 99.5% balanced accuracy in-domain on HC3 PLUS, but performance drops substantially under shift. BERT and RoBERTa show complementary failure modes (human-preserving vs AI-aggressive). DeBERTa-v3-base+FeatAttn achieves 85.9% balanced accuracy on M4 (81.3% human recall, 90.5% AI recall). Multi-seed experiments (5 seeds) confirm stability: 83.15 ± 1.04% macro-average on M4. Under the fixed-threshold protocol, the model outperforms zero-shot baselines (Fast-DetectGPT, RADAR, Log-Rank) by up to +7.22 points. Category-level ablations show readability and vocabulary features contribute most to robustness under shift.

### 中文

基础模型在 HC3 PLUS 域内达到最高 99.5% 平衡准确率，但在分布偏移下性能大幅下降。BERT 和 RoBERTa 显示互补的失败模式（人类保留 vs AI 激进）。DeBERTa-v3-base+FeatAttn 在 M4 上达到 85.9% 平衡准确率（81.3% 人类召回率，90.5% AI 召回率）。多种子实验（5 种子）确认稳定性：M4 宏平均 83.15 ± 1.04%。在固定阈值协议下，该模型超越零样本基线（Fast-DetectGPT、RADAR、Log-Rank）最高 +7.22 分。类别级消融显示可读性和词汇特征对偏移鲁棒性贡献最大。

## 局限性与注意点

### English

The fixed-threshold protocol, while deployment-realistic, means results are sensitive to the specific validation set used for calibration. The feature set (62 features) is English-specific; cross-lingual generalization is not tested. HC3 PLUS uses only ChatGPT (GPT-3.5-Turbo) as the AI generator, which may not represent newer, more capable LLMs. M4's AI-to-human ratio (66,183 / 12,583) is highly imbalanced. The study is offline — streaming/online decision-making is not addressed. The 8-page paper is submitted to ICML 2026.

### 中文

固定阈值协议虽贴近部署现实，但意味着结果对用于校准的特定校验集敏感。特征集（62 个特征）是英语特定的；跨语言泛化未测试。HC3 PLUS 仅使用 ChatGPT (GPT-3.5-Turbo) 作为 AI 生成器，可能不代表更新、更强的 LLM。M4 的 AI 与人类样本比（66,183 / 12,583）极不平衡。研究为离线评估——未涉及流式/在线决策。该 8 页论文已投 ICML 2026。

## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [基准评估](../../concepts/benchmarking.html)
- [AI安全与对齐](../../concepts/ai-safety-alignment.html)

---
*导入时间: 2026-05-06 06:01*
*来源: arXiv Daily Wiki Update 2026-05-06*
