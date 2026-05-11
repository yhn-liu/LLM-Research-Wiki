---
layout: paper
title: "CA-SQL: Complexity-Aware Inference Time Reasoning for Text-to-SQL via Exploration and Compute Budget Allocation"
created: 2026-05-11
updated: 2026-05-11
type: paper
arxiv_id: 2605.08057v1
authors: "James Petullo, Nianwen Xue"
published: 2026-05-08
categories: cs.CL, cs.AI
tags: [nlp, ai, benchmark]
source_url: https://arxiv.org/abs/2605.08057v1
pdf_url: https://arxiv.org/pdf/2605.08057v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: []
---

# CA-SQL: Complexity-Aware Inference Time Reasoning for Text-to-SQL via Exploration and Compute Budget Allocation

## 基本信息

- **arXiv ID:** [2605.08057v1](https://arxiv.org/abs/2605.08057v1)
- **作者:** James Petullo, Nianwen Xue
- **发布日期:** 2026-05-08
- **分类:** cs.CL, cs.AI
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2605.08057v1)


## 摘要

### English

While recent advancements in inference-time learning have improved LLM reasoning on Text-to-SQL tasks, current solutions still struggle to perform well on the most challenging tasks in the Bird-Bench (BIRD) benchmark. This is due to inadequate solution space exploration, which is necessary to uncover promising candidate queries that can be further refined to produce the correct output. To address this challenge, we introduce CA-SQL, a novel Text-to-SQL pipeline that utilizes the estimated difficulty of a task to dynamically scale the breadth of the exploration for generating solution candidates. In addition, we use a custom prompt seeding method, based on principles of evolutionary search, to further elicit exploratory behavior from the base LLM and a novel voting method to select the best candidate solution at the end of the search. Experiments demonstrate that our solution achieves a state-of-the-art score of 51.72% on the "challenging" tier of BIRD development set problems, using only GPT-4o-mini, out-performing other in-context learning approaches, even those that leverage larger models. Overall, our method attains a competitive 61.06% execution accuracy and 68.77% Soft F1 score on the BIRD development dataset.

### 中文

虽然推理时间学习的最新进展改进了文本到 SQL 任务的 LLM 推理，但当前的解决方案仍然难以在 Bird-Bench (BIRD) 基准测试中最具挑战性的任务上表现良好。这是由于解决方案空间探索不充分，而解决方案空间探索对于发现有希望的候选查询是必要的，这些候选查询可以进一步细化以产生正确的输出。为了应对这一挑战，我们引入了 CA-SQL，这是一种新颖的文本到 SQL 管道，它利用任务的估计难度来动态扩展生成候选解决方案的探索广度。此外，我们使用基于进化搜索原理的自定义提示播种方法，进一步从基础 LLM 中引发探索行为，并使用新颖的投票方法在搜索结束时选择最佳候选解决方案。实验表明，我们的解决方案仅使用 GPT-4o-mini，在 BIRD 开发集问题的“挑战性”层上取得了 51.72% 的最先进分数，优于其他上下文学习方法，甚至是那些利用更大模型的方法。总体而言，我们的方法在 BIRD 开发数据集上获得了具有竞争力的 61.06% 执行精度和 68.77% Soft F1 分数。

## 核心贡献

### English
CA-SQL introduces three innovations for Text-to-SQL: (1) a difficulty scorer that dynamically allocates exploration budget based on task complexity; (2) an evolutionary schema-subset seeding strategy using crossover and mutation operators to diversify candidate queries; (3) a novel accumulated-score voting method that outperforms standard majority voting. Using only GPT-4o-mini, CA-SQL achieves state-of-the-art 51.72% execution accuracy on the "challenging" tier of BIRD.

### 中文
CA-SQL 提出三项创新：(1) 基于任务复杂度动态分配探索预算的难度评分器；(2) 使用交叉和变异算子的进化式模式子集播种策略以多样化候选查询；(3) 优于标准多数投票的累积评分投票方法。仅使用 GPT-4o-mini 即在 BIRD "挑战"层上达到最先进的 51.72% 执行精度。

## 方法概述

### English
CA-SQL operates in four stages: (1) Schema Subset Generation — an LLM selects relevant schema subsets, then evolutionary operators (crossover and mutation) recombine them into novel table-column combinations; (2) Candidate Generation — each schema subset seeds a query generation prompt, with the number of subsets scaled by the difficulty score C (1-5); (3) Refinement — a depth component runs parallel refinement chains, also scaled by C; (4) Selection — accumulated candidate evaluation scores weighted by a decay factor select the final answer without requiring the gold query. The difficulty scorer LLM classifies tasks on a 1-5 scale based on schema complexity and query ambiguity.

### 中文
CA-SQL 分四阶段：(1) 模式子集生成——LLM 选择相关模式子集，通过交叉和变异算子重组为新颖的表-列组合；(2) 候选生成——每个子集播种一个查询生成提示，子集数量按难度分 C (1-5) 缩放；(3) 精炼——并行精炼链深度同样按 C 缩放；(4) 选择——基于衰减加权累积评分的投票方法选出最终答案。

## 实验结果

### English
CA-SQL achieves 61.06% execution accuracy and 68.77% Soft F1 on BIRD dev using GPT-4o-mini. On the challenging tier specifically: 51.72% EX, outperforming all in-context learning baselines including those using GPT-4o (45.14%), MAC-SQL+GPT-4 (38.82%), and CHASE-SQL+GPT-4. Evolutionary seeding increases candidate uniqueness by 34% over single-subset sampling. Accumulated-score voting outperforms majority voting by 5.2% EX.

### 中文
CA-SQL 在 BIRD dev 上达到 61.06% 执行精度和 68.77% Soft F1。在挑战层：51.72% EX，优于所有上下文学习基线包括使用 GPT-4o 的 MAC-SQL（45.14%）和 CHASE-SQL+GPT-4（38.82%）。进化播种使候选唯一性比单子集采样提高 34%。累积评分投票比多数投票高 5.2% EX。

## 局限性与注意点

- 难度评分器的精度直接影响预算分配效率，误分类可能导致资源浪费。
- 进化算子（交叉/变异）的随机性使结果不可完全复现。
- 仅在 BIRD 英文数据集上验证，对中文等其他语言的 Text-to-SQL 表现未知。
- 整体执行精度（61.06%）仍远低于训练时微调方法（如 SFT CodeS-15B 的 67.1%）。
- 多轮 LLM 调用增加延迟，不适用于低延迟生产环境。

## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [基准评估](../../concepts/benchmarking.html)

---
*导入时间: 2026-05-11 06:01*
*来源: arXiv Daily Wiki Update 2026-05-11*
