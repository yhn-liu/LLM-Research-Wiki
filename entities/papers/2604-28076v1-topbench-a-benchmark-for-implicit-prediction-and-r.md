---
layout: paper
title: "TopBench: A Benchmark for Implicit Prediction and Reasoning over Tabular Question Answering"
arxiv_id: 2604.28076v1
authors: "An-Yang Ji, Jun-Peng Jiang, De-Chuan Zhan et al. (4 authors)"
published: 2026-05-01
categories: cs.CL, cs.AI, cs.LG
tags: [nlp, ml, ai]
type: paper
source_url: https://arxiv.org/abs/2604.28076v1
pdf_url: https://arxiv.org/pdf/2604.28076v1
---


# TopBench: A Benchmark for Implicit Prediction and Reasoning over Tabular Question Answering

## 基本信息

- **arXiv ID:** [2604.28076v1](https://arxiv.org/abs/2604.28076v1)
- **作者:** An-Yang Ji, Jun-Peng Jiang, De-Chuan Zhan et al. (4 authors)
- **发布日期:** 2026-04-30
- **分类:** cs.CL, cs.AI, cs.LG

## 摘要

### English

Large Language Models (LLMs) have advanced Table Question Answering, where most queries can be answered by extracting information or simple aggregation. However, a common class of real-world queries is implicitly predictive, requiring the inference of unobserved answers from historical patterns rather than mere retrieval. These queries introduce two challenges: recognizing latent intent and reliable predictive reasoning over massive tables. To assess LLMs in such Tabular questiOn answering with 

### 中文

大型语言模型 (LLM) 具有高级表问答功能，可以通过提取信息或简单聚合来回答大多数查询。然而，一类常见的现实世界查询是隐式预测的，需要从历史模式中推断出未观察到的答案，而不仅仅是检索。这些查询带来了两个挑战：识别潜在意图和对大量表进行可靠的预测推理。为了评估 LLM 在此类隐式预测任务中回答表格问题的情况，我们引入了 TopBench，这是一个由四个子任务的 779 个样本组成的基准，范围从单点预测到决策、治疗效果分析和复杂过滤，要求模型生成涵盖推理文本和结构化表格的输出。我们在基于文本和代理工作流程下评估不同的模型。实验表明，当前的模型经常难以识别意图，默认只进行查找。更深入的分析表明，准确的意图消歧是引导这些预测行为的先决条件。此外，提高预测精度的上限需要集成更复杂的建模或推理能力。

## 核心贡献

- 提出 TopBench 基准，专门评估 LLM 在表格问答中的隐式预测能力
- 包含 4 个子任务共 779 个样本，涵盖单点预测、决策、治疗效果分析等
- 揭示当前模型在识别潜在意图方面的不足

## 方法概述

构建了一个包含四种隐式预测任务的基准数据集，要求模型不仅检索信息，还需从历史模式中推断未观察到的答案。评估了文本和代理两种工作流程下的模型表现。

## 实验结果

当前模型经常难以识别隐式查询的潜在意图，默认只进行查找操作。准确的意图消歧是引导预测行为的先决条件，提高预测精度需要更复杂的建模能力。

## 相关论文

<!-- 待填充：添加相关论文链接 -->


## 分析信息

- **分析来源:** LLM亲自分析
- **分析置信度:** high
- **分析时间:** 2026-05-01

---
*导入时间: 2026-05-01 19:53*
*来源: arXiv Daily Digest 2026-05-01*
