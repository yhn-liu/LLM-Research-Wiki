---
layout: paper
title: "Grokability in five inequalities"
created: 2026-05-07
updated: 2026-05-07
type: paper
arxiv_id: 2605.05193v1
authors: "Paata Ivanisvili, Xinyuan Xie"
published: 2026-05-06
categories: math.PR, cs.AI, math.AP, math.CA, math.FA
tags: [ai]
source_url: https://arxiv.org/abs/2605.05193v1
pdf_url: https://arxiv.org/pdf/2605.05193v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: []
---

# Grokability in five inequalities

## 基本信息

- **arXiv ID:** [2605.05193v1](https://arxiv.org/abs/2605.05193v1)
- **作者:** Paata Ivanisvili, Xinyuan Xie
- **发布日期:** 2026-05-06
- **分类:** math.PR, cs.AI, math.AP, math.CA, math.FA
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2605.05193v1)


## 摘要

### English

In this note, we report five mathematical discoveries made in collaboration with Grok, all of which have been subsequently verified by the authors. These include an improved lower bound on the maximal Gaussian perimeter of convex sets in $\mathbb{R}^n$, sharper $L_2$-$L_1$ moment comparison inequalities on the Hamming cube $\{-1,1\}^n$, a strengthened autoconvolution inequality, improved asymptotic bounds on the size of the largest $g$-Sidon sets in $\{1,\dots,n\}$, and an optimal balanced Szarek's inequality.

### 中文

在这篇文章中，我们报告了与 Grok 合作的五项数学发现，所有这些发现都随后得到了作者的验证。其中包括 $\mathbb{R}^n$ 中凸集最大高斯周长的改进下界、汉明立方 $\{-1,1\}^n$ 上更尖锐的 $L_2$-$L_1$ 矩比较不等式、强化的自卷积不等式、$\{1,\dots,n\}$ 中最大 $g$-Sidon 集大小的改进渐近边界，以及最佳平衡萨雷克不等式。

## 核心贡献

本文报告了与 Grok 合作得出的五项数学发现（全部经作者验证），涵盖分析、概率、凸几何和加法组合学四个领域：

1. **凸集最大高斯周长下界的改进**：将 Nazarov 2003 年构造的常数从 e^{-5/4} ≈ 0.2865 提升约 9% 至 **0.31258**，是自 Nazarov 以来对该常数的首次改进。
2. **Hamming 立方体 L₂-L₁ 矩比较不等式**：证明最优指数底 C⋆ 满足 **√3 ≤ C⋆ ≤ 2.408...**，其中下界回答了 Noam Lifshitz 2014 年在 MathOverflow 上的问题（否定 C⋆ = √2 的猜想）。
3. **最优平衡 Szarek 不等式**：在 Hamming 立方体中间切片（条件化 Rademacher 变量和为 0）上，证明经典半群方法仍能获得最优常数，尽管此时变量不再独立。
4. **自卷积不等式的改进下界**：对 g-Sidon 集大小的 C1a 常数给出微小改进，该常数被记录在 Tao 发起的优化常数项目中。
5. **强化自卷积不等式**：给出了该经典不等式的加强版本。

## 方法概述

论文采用 Grok 辅助的"对话式数学探索"方法，而非结构化搜索或程序化验证。对于每个问题，作者与 Grok 交流，Grok 帮助推理证明步骤、精细调优构造参数，并提供对文献中未完成证明的补充。

以高斯周长为例（Theorem 1）：作者遵循 Nazarov 2003 年的一般策略，但通过 Grok 协助完善了 Nazarov 原文中略去的中间论证，修正了原始论文中一个次要数值误差，并微调了构造参数以得到更好的常数。

论文的每个结果均给出了完整的数学证明（Section 2），并在附录 A 中提供了与 Grok 对话的完整链接作为透明性保障。

## 实验结果

本文为纯数学论文，不包含机器学习意义上的实验。但其"结果"本身就是五项经过验证的数学定理。关键数值结果包括：

- **Theorem 1**：lim inf_{n→∞} Γ(n)/n^{1/4} ≥ 0.31258（相比此前最优 0.2865 提升约 9%）
- **Theorem 2**：√3 ≈ 1.732 ≤ C⋆ ≤ 2.408...（此前最好上界为 2.69...，下界无发表记录）
- **C1a 常数**：对数分钟对话内实现微小改进，此前最优下界需约 20,000 CPU 小时穷举搜索

## 局限性与注意点

1. **非可复现性**：对话式 AI 辅助的数学发现依赖于特定的模型和交互过程，结果的"可复现性"与传统数学证明不同。
2. **验证依赖作者**：所有结果虽经作者独立验证，但对话中的中间步骤是否完全正确未由第三方审查。
3. **常数改进幅度有限**：部分改进（如 C1a 常数）幅度微小，更多展示方法论潜力而非结果本身的突破性。
4. **Grok 特定性**：未与其他推理模型（如 DeepSeek-R1、o3 等）进行系统对比，无法判断 Grok 的能力是否独特。
5. **无 LLM 相关概念**：论文是纯数学成果报告，不可归入标准 AI 概念的分类体系。

## 相关概念

本论文为纯数学成果，不涉及 LLM 技术概念。

---
*导入时间: 2026-05-07 06:01*
*来源: arXiv Daily Wiki Update 2026-05-07*
