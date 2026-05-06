---
layout: paper
title: "Rethinking Reasoning-Intensive Retrieval: Evaluating and Advancing Retrievers in Agentic Search Systems"
created: 2026-05-06
updated: 2026-05-06
type: paper
arxiv_id: 2605.04018v1
authors: "Yilun Zhao, Jinbiao Wei, Tingyu Song, Siyue Zhang, Chen Zhao, Arman Cohan"
published: 2026-05-05
categories: cs.CL, cs.IR
tags: [nlp, benchmark]
source_url: https://arxiv.org/abs/2605.04018v1
pdf_url: https://arxiv.org/pdf/2605.04018v1
source_type: arxiv_daily
confidence: medium
status: analyzed
confidence: high
key_figures: []
---

# Rethinking Reasoning-Intensive Retrieval: Evaluating and Advancing Retrievers in Agentic Search Systems

## 基本信息

- **arXiv ID:** [2605.04018v1](https://arxiv.org/abs/2605.04018v1)
- **作者:** Yilun Zhao, Jinbiao Wei, Tingyu Song et al.
- **发布日期:** 2026-05-05
- **分类:** cs.CL, cs.IR
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2605.04018v1)


## 摘要

### English

Reasoning-intensive retrieval aims to surface evidence that supports downstream reasoning rather than merely matching topical similarity. This capability is increasingly important for agentic search systems, where retrievers must provide complementary evidence across iterative search and synthesis. However, existing work remains limited on both evaluation and training: benchmarks such as BRIGHT provide narrow gold sets and evaluate retrievers in isolation, while synthetic training corpora often optimize single-passage relevance rather than evidence portfolio construction. We introduce BRIGHT-Pro, an expert-annotated benchmark that expands each query with multi-aspect gold evidence and evaluates retrievers under both static and agentic search protocols. We further construct RTriever-Synth, an aspect-decomposed synthetic corpus that generates complementary positives and positive-conditioned hard negatives, and use it to LoRA fine-tune RTriever-4B from Qwen3-Embedding-4B. Experiments across lexical, general-purpose, and reasoning-intensive retrievers show that aspect-aware and agentic evaluation expose behaviors hidden by standard metrics, while RTriever-4B substantially improves over its base model.

### 中文

推理密集型检索旨在找出支持下游推理的证据，而不仅仅是匹配主题相似性。这种能力对于代理搜索系统越来越重要，检索器必须在迭代搜索和合成中提供补充证据。然而，现有的工作在评估和训练方面仍然有限：诸如 BRIGHT 之类的基准提供了狭窄的黄金集并单独评估检索器，而综合训练语料库通常优化单通道相关性而不是证据组合构建。我们推出了 BRIGHT-Pro，这是一个专家注释的基准测试，它通过多方面的黄金证据扩展每个查询，并在静态和代理搜索协议下评估检索器。我们进一步构建了 RTriever-Synth，一个方面分解的合成语料库，可生成互补的正例和正条件硬负例，并用它来 LoRA 从 Qwen3-Embedding-4B 微调 RTriever-4B。词汇、通用和推理密集型检索器的实验表明，方面感知和代理评估暴露了标准指标隐藏的行为，而 RTriever-4B 比其基本模型有了显着改进。

## 核心贡献

### English

This paper introduces BRIGHT-Pro, an expert-annotated benchmark that expands each query with multi-aspect gold evidence and evaluates retrievers under both static (one-shot) and agentic (iterative) search protocols — exposing behaviors hidden by standard single-passage metrics. It further constructs RTriever-Synth, an aspect-decomposed synthetic training corpus that generates complementary positives and positive-conditioned hard negatives, and uses it to LoRA fine-tune RTriever-4B from Qwen3-Embedding-4B. The key finding is that aspect-aware and agentic evaluation reveals brittleness invisible to standard retrieval benchmarks.

### 中文

本文提出 BRIGHT-Pro，一个专家标注的基准，以多方面黄金证据扩展每个查询，并在静态（单次）和智能体（迭代）搜索协议下评估检索器——暴露了标准单段落指标所隐藏的行为。进一步构建 RTriever-Synth，一个方面分解的合成训练语料库，生成互补正例和正条件硬负例，并用它从 Qwen3-Embedding-4B LoRA 微调 RTriever-4B。核心发现是：方面感知和智能体评估揭示了标准检索基准不可见的脆弱性。

## 方法概述

### English

BRIGHT-Pro re-audits existing BRIGHT passages, collects new multi-aspect evidence with expert annotation of aspect groups and weights, and implements two evaluation protocols: static (single retrieval) and agentic (iterative multi-round retrieval simulating an agentic search system). RTriever-Synth takes seed MS MARCO queries, uses an LLM to create query-aligned personas, generates expanded questions with background context, and synthesizes aspect-decomposed training data with complementary positives. RTriever-4B is LoRA fine-tuned on this corpus from the Qwen3-Embedding-4B base.

### 中文

BRIGHT-Pro 重新审计现有 BRIGHT 段落，收集带有方面分组和权重的专家标注的新多方面证据，并实现两种评估协议：静态（单次检索）和智能体（模拟智能体搜索系统的迭代多轮检索）。RTriever-Synth 以 MS MARCO 种子查询为基础，使用 LLM 创建查询对齐的角色，生成带背景上下文的扩展问题，并合成具有互补正例的方面分解训练数据。RTriever-4B 在此语料库上从 Qwen3-Embedding-4B 基座进行 LoRA 微调。

## 实验结果

### English

Experiments evaluate lexical (BM25), general-purpose (GTE-Qwen2, BGE), and reasoning-intensive retrievers (BRIGHT baselines, RTriever-4B) under both static and agentic protocols. Aspect-aware evaluation exposes performance variance across different evidence aspects that standard single-metric reporting conceals. Agentic evaluation shows that retrievers optimized for single-turn relevance may underperform in iterative search scenarios where complementary evidence gathering matters. RTriever-4B substantially improves over the Qwen3-Embedding-4B base model, particularly in aspect-coverage metrics.

### 中文

实验在静态和智能体协议下评估了词汇检索器（BM25）、通用检索器（GTE-Qwen2、BGE）和推理密集型检索器（BRIGHT 基线、RTriever-4B）。方面感知评估暴露了标准单一指标报告所隐藏的不同证据方面之间的性能差异。智能体评估表明，针对单轮相关性优化的检索器在需要互补证据收集的迭代搜索场景下可能表现不佳。RTriever-4B 相比 Qwen3-Embedding-4B 基座模型有显著改进，尤其在方面覆盖率指标上。

## 局限性与注意点

### English

BRIGHT-Pro's expert annotations, while high-quality, may not scale to the diversity of real-world search queries. The agentic evaluation protocol simulates iterative search but does not involve actual LLM-driven agent loops. RTriever-Synth is trained on synthetic data, which may introduce biases not present in natural retrieval distributions. The paper focuses on English-language retrieval only (ACL 2026). The 4B parameter scale may limit applicability in resource-constrained settings.

### 中文

BRIGHT-Pro 的专家标注虽然高质量，但可能无法扩展到真实世界搜索查询的多样性。智能体评估协议模拟迭代搜索但未涉及实际的 LLM 驱动智能体循环。RTriever-Synth 在合成数据上训练，可能引入自然检索分布中不存在偏差。论文仅聚焦英语检索（ACL 2026）。4B 参数量级可能限制在资源受限场景的适用性。

## 相关概念

- [基准评估](../../concepts/benchmarking.html)
- [智能体](../../concepts/ai-agents.html)

---
*导入时间: 2026-05-06 06:01*
*来源: arXiv Daily Wiki Update 2026-05-06*
