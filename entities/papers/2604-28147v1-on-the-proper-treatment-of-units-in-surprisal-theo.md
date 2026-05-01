---
layout: paper
title: "On the Proper Treatment of Units in Surprisal Theory"
created: 2026-05-01
updated: 2026-05-01
type: paper
arxiv_id: 2604.28147v1
authors: "Samuel Kiegeland, Vésteinn Snæbjarnarson, Tim Vieira et al. (4 authors)"
published: 2026-04-30
categories: cs.CL
tags: [nlp]
source_url: https://arxiv.org/abs/2604.28147v1
pdf_url: https://arxiv.org/pdf/2604.28147v1
confidence: high
status: analyzed
---

# On the Proper Treatment of Units in Surprisal Theory

## 基本信息

- **arXiv ID:** [2604.28147v1](https://arxiv.org/abs/2604.28147v1)
- **作者:** Samuel Kiegeland, Vésteinn Snæbjarnarson, Tim Vieira et al. (4 authors)
- **发布日期:** 2026-04-30
- **分类:** cs.CL

## 摘要

### English

Surprisal theory links human processing effort to the predictability of an upcoming linguistic unit, but empirical work often leaves the notion of a unit underspecified. In practice, experimental stimuli are segmented into linguistically motivated units (e.g., words), while pretrained language models assign probability mass to a fixed token alphabet that typically does not align with those units. As a result, surprisal-based predictors depend implicitly on ad hoc procedures that conflate two distinct modeling choices: the definition of the unit of analysis and the choice of the region of interest for evaluating predictions. In this paper, we disentangle these choices and provide a unified framework for reasoning about surprisal over arbitrary unit inventories. We argue that surprisal-based analyses should make these choices explicit and treat tokenization as an implementation detail rather than a scientific primitive.

### 中文

惊讶理论将人类的处理努力与即将到来的语言单位的可预测性联系起来，但实证研究常常没有明确单位的概念。在实践中，实验刺激被分割成语言动机单元（例如单词），而预训练的语言模型将概率质量分配给通常与这些单元不对齐的固定标记字母表。因此，基于惊讶的预测变量隐含地依赖于临时程序，该程序合并了两种不同的建模选择：分析单元的定义和评估预测的感兴趣区域的选择。在本文中，我们理清了这些选择，并给出了一个统一的框架来推理任意单位库存的惊讶。我们认为，基于惊讶的分析应该使这些选择变得明确，并将标记化视为实现细节而不是科学原语。

## 核心贡献

- **揭示惊讶理论中的单位问题**：指出惊讶理论实证研究中"分析单元"概念模糊的问题——实验用的是词级单位，但语言模型的概率分配基于 token 级字母表，两者不对齐
- **解耦两个建模选择**：将"分析单元的定义"与"评估预测的感兴趣区域选择"这两个常被混淆的建模选择显式分离
- **提供统一框架**：提出一个统一的数学框架，支持对任意单元词表进行惊讶值推理
- **重新定位 tokenization 的角色**：主张在惊讶分析中将分词 (tokenization) 视为实现细节而非科学原语

## 方法概述

本文从理论角度出发，分析了惊讶理论 (Surprisal Theory) 在自然语言处理实证研究中的单位处理问题。惊讶理论的核心观点是：人类处理语言单元的努力程度与该单元的可预测性（惊讶值）成正比。然而，实际操作中存在一个根本性矛盾：心理语言学实验通常以"词"作为分析单位，而预训练语言模型（如 GPT）的输出概率分布是基于 token 的，两者之间存在系统性不对齐。

作者将这一问题解耦为两个独立的建模选择：(1) 分析单元（analysis unit）的定义，即我们希望以什么粒度衡量惊讶值；(2) 感兴趣区域（region of interest）的选择，即在评估预测时关注文本的哪个部分。现有研究通常使用即兴的后处理程序将 token 级概率映射到词级单位，但这些程序缺乏统一的理论基础。

基于此分析，作者提出了一个统一的框架，能够对任意单元词表（word inventory）进行惊讶值计算。该框架将分词视为一个可替换的实现细节，而非语言学分析中的科学原语，从而使惊讶分析更加透明和可复现。

## 实验结果

- **研究类型**: 理论分析与方法论框架论文，非实验性基准测试
- **核心贡献**: 方法论层面，为惊讶分析提供了统一的理论框架
- **关键发现**: 分词选择（tokenization）对惊讶值计算有显著影响，但现有研究常忽略这一因素；显式区分分析单元和感兴趣区域可提高惊讶分析的透明度和可复现性
- **适用范围**: 框架适用于基于任意语言模型的惊讶分析，不限于特定模型架构

## 相关概念

- [惊讶理论](../concepts/surprisal-theory.html)
- [分词](../concepts/tokenization.html)
- [语言模型评估](../concepts/language-model-evaluation.html)
- [自然语言处理](../concepts/nlp.html)

---

*导入时间: 2026-05-01 19:53*
*来源: arXiv Daily Digest 2026-05-01*
