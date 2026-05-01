---
layout: paper
title: "Measuring research data reuse in scholarly publications using generative artificial intelligence: Open Science Indicator development and preliminary results"
created: 2026-05-01
updated: 2026-05-01
type: paper
arxiv_id: 2604.28061v1
authors: "Lauren Cadwallader, Iain Hrynaszkiewicz, Parth Sarin et al."
published: 2026-04-30
categories: cs.DL, cs.CL
tags: [nlp, open-science, data-reuse, LLM, metascience]
source_url: https://arxiv.org/abs/2604.28061v1
pdf_url: https://arxiv.org/pdf/2604.28061v1
confidence: high
status: analyzed
---

# Measuring research data reuse in scholarly publications using generative artificial intelligence: Open Science Indicator development and preliminary results

## 基本信息

- **arXiv ID:** [2604.28061v1](https://arxiv.org/abs/2604.28061v1)
- **作者:** Lauren Cadwallader, Iain Hrynaszkiewicz, Parth Sarin et al.
- **发布日期:** 2026-04-30
- **分类:** cs.DL, cs.CL

## 摘要

### English

Numerous metascience studies and other initiatives have begun to monitor the prevalence of open science practices when it is more important to understand the 'downstream' effects or impacts of open science. PLOS and DataSeer have developed a new LLM-based indicator to measure an important effect of open science: the reuse of research data. Our results show a data reuse rate of 43%, which is higher than established bibliometric techniques. We show that data reuse can be measured at scale using LLMs and generative AI. The positive impacts of research data sharing and reuse may currently be underestimated.

### 中文

当了解开放科学的"下游"效应或影响更为重要时，许多元科学研究和其他举措已经开始监测开放科学实践的流行程度。PLOS和DataSeer开发了一种新的基于LLM的指标来衡量开放科学的重要影响：研究数据的重用。我们的结果显示数据重用率为43%，高于现有的文献计量技术。我们证明，可以使用LLM和生成式人工智能大规模地衡量数据重用。研究数据共享和重用的积极影响目前可能被低估。

## 核心贡献

1. **开发基于LLM的数据重用指标**：PLOS与DataSeer合作，利用大语言模型（LLM）和生成式AI技术开发了一种新的开放式科学指标（Open Science Indicator），用于衡量学术出版物中研究数据的重用情况。
2. **实现大规模自动化数据重用测量**：证明了利用LLM可以大规模、自动化地检测和量化研究数据的重用，克服了传统文献计量技术在覆盖范围和准确性上的局限。
3. **揭示数据重用率被低估的事实**：研究发现数据重用率为43%，显著高于传统文献计量方法的估计结果，表明研究数据共享和重用的积极影响目前可能被系统性地低估。
4. **推动开放科学影响力评估**：将开放科学的评估重点从实践的普及程度（如数据共享政策的实施率）转向实际的下游影响（如数据是否被真正重用），为开放科学政策制定提供更有价值的决策依据。

## 方法概述

本文提出了一种基于大语言模型（LLM）和生成式AI的自动化方法，用于识别和衡量学术出版物中研究数据的重用情况。该方法的核心思路是利用LLM对论文文本进行语义理解和信息抽取，判断论文是否重用了他人的研究数据。

传统的数据重用测量方法主要依赖文献计量技术，如通过数据引用（data citation）来追踪数据的使用。然而，许多数据重用行为并未伴随正式的数据引用，导致传统方法严重低估了实际的数据重用率。本研究通过LLM对论文全文进行分析，能够识别出隐含的数据重用行为，包括那些未通过正式引用标注的数据使用。

PLOS作为开放获取出版商，提供了大量可获取的全文论文数据，为大规模训练和验证该方法提供了基础。DataSeer则提供了数据重用标注的领域专业知识和标注数据。两者的合作使得该LLM-based指标兼具技术可行性和领域准确性。

## 实验结果

- **数据重用率为43%**：使用基于LLM的指标检测到的数据重用率高达43%，这一数字远高于传统文献计量技术的估计结果。
- **优于传统文献计量方法**：基于LLM的方法在检测数据重用方面表现优于现有的文献计量技术，能够发现更多未被正式引用的数据重用实例。
- **可扩展性强**：该方法能够大规模应用，为系统性地监测开放科学的影响提供了可行的自动化工具。
- **揭示低估问题**：研究数据共享和重用的积极影响目前可能被低估，为开放科学政策的制定和评估提供了重要的修正参考。

## 分析信息

- **分析来源:** pdf_analysis
- **分析置信度:** high
- **分析时间:** 2026-05-01 21:13
- **关键词:** LLM, open science, data reuse, metascience, bibliometrics, generative AI
- **PDF 路径:** /root/wiki/raw/papers/2604-28061v1.pdf

---

*导入时间: 2026-05-01 19:53*
*来源: arXiv Daily Digest 2026-05-01*

## 相关概念

- [大语言模型](../concepts/large-language-model.md)
- [开放科学](../concepts/open-science.md)
- [数据重用](../concepts/data-reuse.md)
- [元科学](../concepts/metascience.md)
- [文献计量学](../concepts/bibliometrics.md)
- [生成式人工智能](../concepts/generative-ai.md)
