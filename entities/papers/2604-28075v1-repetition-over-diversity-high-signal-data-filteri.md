---
layout: paper
---
---
layout: paper
title: "Repetition over Diversity: High-Signal Data Filtering for Sample-Efficient German Language Modeling"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28075v1
authors: "Ansar Aynetdinov, Patrick Haller, Alan Akbik"
published: 2026-04-30
categories: cs.CL, cs.AI
tags: [nlp, ai]
source_url: https://arxiv.org/abs/2604.28075v1
pdf_url: https://arxiv.org/pdf/2604.28075v1
source_type: arxiv_daily
confidence: medium
status: needs_pdf_lm_analysis
---

# Repetition over Diversity: High-Signal Data Filtering for Sample-Efficient German Language Modeling

## 基本信息

- **arXiv ID:** [2604.28075v1](https://arxiv.org/abs/2604.28075v1)
- **作者:** Ansar Aynetdinov, Patrick Haller, Alan Akbik et al.
- **发布日期:** 2026-04-30
- **分类:** cs.CL, cs.AI


## 关键图示

<div class="paper-figure-grid">
<figure><img src="../../assets/papers/2604-28075v1/fig1.png" alt="Repetition over Diversity: High-Signal Data Filtering for Sample-Efficient German Language Modeling Figure 1"><figcaption>Figure 1</figcaption></figure>
<figure><img src="../../assets/papers/2604-28075v1/fig2.png" alt="Repetition over Diversity: High-Signal Data Filtering for Sample-Efficient German Language Modeling Figure 2"><figcaption>Figure 2</figcaption></figure>
<figure><img src="../../assets/papers/2604-28075v1/fig3.png" alt="Repetition over Diversity: High-Signal Data Filtering for Sample-Efficient German Language Modeling Figure 3"><figcaption>Figure 3</figcaption></figure>
</div>


## 摘要

Recent research has shown that filtering massive English web corpora into high-quality subsets significantly improves training efficiency. However, for high-resource non-English languages like German, French, or Japanese, aggressive filtering creates a strategic dilemma: should practitioners prioritize diversity by training once on large amounts of lightly filtered web data, or prioritize quality by strictly filtering for a high-quality core and repeating it over multiple epochs? We investigate this trade-off for German by constructing hierarchical quality filters applied to 500M web documents, comparing multi-epoch training on the filtered subsets against single-pass training on a diverse corpus. Our experiments across multiple model scales and token budgets show that repeating high-quality data consistently outperforms single-pass training on larger, less filtered sets. Notably, the performance gap persists even after 7 epochs. Our findings suggest that for non-English LLMs, semantic concentration through quality filtering offers a more viable path to efficient language modeling than simply maximizing unique data volume. We release our German language models (called Boldt), as well as our cleaned evaluation benchmarks to the research community. Our experiments indicate that they achieve state-of-the-art results despite training on 10-360x fewer tokens than comparable models.


## 深度解读状态

> 待 PDF 下载并由 LM 阅读后补充。本文详情页不会使用 arXiv 元数据或摘要快速导读冒充完整解读。

## 相关论文

<!-- 待填充：添加相关论文链接 -->


---
*导入时间: 2026-05-02 06:01*
*来源: arXiv Daily Digest 2026-05-02*
