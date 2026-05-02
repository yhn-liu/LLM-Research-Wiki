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
confidence: high
status: analyzed
---

# Repetition over Diversity: High-Signal Data Filtering for Sample-Efficient German Language Modeling

## 基本信息

- **arXiv ID:** [2604.28075v1](https://arxiv.org/abs/2604.28075v1)
- **作者:** Ansar Aynetdinov, Patrick Haller, Alan Akbik et al.
- **发布日期:** 2026-04-30
- **分类:** cs.CL, cs.AI

## 摘要

Recent research has shown that filtering massive English web corpora into high-quality subsets significantly improves training efficiency. However, for high-resource non-English languages like German, French, or Japanese, aggressive filtering creates a strategic dilemma: should practitioners prioritize diversity by training once on large amounts of lightly filtered web data, or prioritize quality by strictly filtering for a high-quality core and repeating it over multiple epochs? We investigate this trade-off for German by constructing hierarchical quality filters applied to 500M web documents, comparing multi-epoch training on the filtered subsets against single-pass training on a diverse corpus. Our experiments across multiple model scales and token budgets show that repeating high-quality data consistently outperforms single-pass training on larger, less filtered sets. Notably, the performance gap persists even after 7 epochs. Our findings suggest that for non-English LLMs, semantic concentration through quality filtering offers a more viable path to efficient language modeling than simply maximizing unique data volume. We release our German language models (called Boldt), as well as our cleaned evaluation benchmarks to the research community. Our experiments indicate that they achieve state-of-the-art results despite training on 10-360x fewer tokens than comparable models.

## 核心贡献

- Recent research has shown that filtering massive English web corpora into high-quality subsets significantly improves training efficiency

## 方法概述

<!-- 未能从摘要中自动提取，请手动补充 -->

## 实验结果

that repeating high-quality data consistently outperforms single-pass training; state-of-the-art results despite training; they achieve state-of-the-art results despite training on 10-360x fewer tokens than comparable models

## 相关论文

<!-- 待填充：添加相关论文链接 -->


## 分析信息

- **分析来源:** summary_extract
- **分析置信度:** medium
- **分析时间:** 2026-05-02 06:02
- **关键词:** LLM

---
*导入时间: 2026-05-02 06:01*
*来源: arXiv Daily Digest 2026-05-02*
