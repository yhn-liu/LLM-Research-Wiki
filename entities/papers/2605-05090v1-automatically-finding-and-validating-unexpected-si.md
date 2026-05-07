---
layout: paper
title: "Automatically Finding and Validating Unexpected Side-Effects of Interventions on Language Models"
created: 2026-05-07
updated: 2026-05-07
type: paper
arxiv_id: 2605.05090v1
authors: "Quintin Pope, Ajay Hayagreeve Balaji, Jacques Thibodeau, Xiaoli Fern"
published: 2026-05-06
categories: cs.CL, cs.AI
tags: [nlp, ai]
source_url: https://arxiv.org/abs/2605.05090v1
pdf_url: https://arxiv.org/pdf/2605.05090v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: []
---

# Automatically Finding and Validating Unexpected Side-Effects of Interventions on Language Models

## 基本信息

- **arXiv ID:** [2605.05090v1](https://arxiv.org/abs/2605.05090v1)
- **作者:** Quintin Pope, Ajay Hayagreeve Balaji, Jacques Thibodeau et al.
- **发布日期:** 2026-05-06
- **分类:** cs.CL, cs.AI
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2605.05090v1)


## 摘要

### English

We present an automated, contrastive evaluation pipeline for auditing the behavioral impact of interventions on large language models. Given a base model $M_1$ and an intervention model $M_2$, our method compares their free-form, multi-token generations across aligned prompt contexts and produces human-readable, statistically validated natural-language hypotheses describing how the models differ, along with recurring themes that summarize patterns across validated hypotheses.   We evaluate the approach in synthetic setting by injecting known behavioral changes and showing that the pipeline reliably recovers them. We then apply it to three real-world interventions, reasoning distillation, knowledge editing and unlearning, demonstrating that the method surfaces both intended and unexpected behavioral shifts, distinguishes large from subtle interventions, and does not hallucinate differences when effects are absent or misaligned with the prompt bank. Overall, the pipeline provides a statistically grounded and interpretable tool for post-hoc auditing of intervention-induced changes in model behavior.

### 中文

我们提出了一个自动化的对比评估流程，用于审核干预措施对大型语言模型的行为影响。给定基本模型 $M_1$ 和干预模型 $M_2$，我们的方法在对齐的提示上下文中比较它们的自由形式、多标记生成，并生成人类可读的、经统计验证的自然语言假设，描述模型的差异，以及总结经过验证的假设的模式的重复主题。我们通过注入已知的行为变化并表明管道可靠地恢复它们来评估合成环境中的方法。然后，我们将其应用于三种现实世界的干预措施：推理蒸馏、知识编辑和忘却，证明该方法可以显示有意的和意外的行为变化，区分大的干预措施和微妙的干预措施，并且当效果不存在或与提示库不一致时，不会产生幻觉差异。总体而言，该管道提供了一个基于统计且可解释的工具，用于对干预引起的模型行为变化进行事后审核。

## 核心贡献

1. 提出**自动化对比评估流水线**，用于审计 LLM 干预（微调、知识编辑、遗忘等）的行为影响，输出人类可读的、经统计验证的自然语言假设和重复主题。
2. 设计严格的多阶段流程：(a) Stage 1：通过语义聚类或预定义类别对齐提示上下文，构建配对文本分布；(b) Stage 2：使用 Hypothesizer + Discriminator 生成并验证候选差异假设，配合 Benjamini-Hochberg FDR 控制；(c) Stage 3：去冗余并提取重复主题。
3. 在**合成恢复实验**中验证流水线能可靠恢复注入的已知行为变化；在三种真实干预（推理蒸馏、知识编辑、遗忘）上成功发现有意和意外的行为偏移，并能区分大幅干预与微妙干预。
4. 当效果缺失或与提示库不一致时，流水线**不会产生虚假差异报告**，证明了统计控制的可靠性。

## 方法概述

Stage 1：从探针数据集（Anthropic Persona、TruthfulQA、Amazon BOLD）中构建语义上下文集合 C。对每个上下文 c，配对生成 M₁ 和 M₂ 的响应样本 Y_c。Persona 使用预定义的 135 个行为类别作为上下文；TruthfulQA 和 BOLD 使用嵌入聚类。

Stage 2：Hypothesizer（LLM 驱动的假设生成器）从训练分区中为每个上下文 c 生成候选自然语言假设 h_c，描述 M₂ 相对于 M₁ 的差异。然后 Discriminator（独立 LLM 评判器）在保留的验证分区上执行盲测——给定 (提示, 响应) 对并接收 h_c，判断该响应来自 M₁ 还是 M₂。通过 Benjamini-Hochberg 过程进行 FDR 控制，仅保留具有显著判别力（AUC > 0.5）的假设。

Stage 3：使用 LLM 对已验证假设进行主题聚类和去冗余，输出简洁的差异报告（重复主题 + 非冗余验证假设）。

## 实验结果

- **合成实验**：注入已知的行为偏移（如改变礼貌程度、添加或移除特定领域的知识），流水线成功恢复了所有注入的变化。
- **推理蒸馏**（DeepSeek-R1 教师蒸馏到 Llama-3.1-8B）：发现蒸馏后模型在数学推理上表现出更强的结构化和逐步推理风格，但也出现意料之外的冗长倾向和特定的格式偏好。
- **知识编辑**（ROME 编辑）：流水线检测到编辑目标知识的预期变化，同时发现编辑在相关但非目标的上下文区域产生了微妙的行为溢出。
- **遗忘**（Eldan & Russinovich 遗忘方法）：在遗忘目标（Harry Potter 知识）上检测到大效应；在非目标上下文上效应很小，且流水线正确报告了效应的稀疏性和局部性。
- **负控制**：当 M₁ = M₂（同一模型）或提示库与干预效应不对齐时，流水线不报告任何显著假设，验证了 FDR 控制的有效性。

## 局限性与注意点

1. **提示库依赖**：发现的结果受限于使用的提示库，狭窄或上下文特定的行为效应可能被遗漏。
2. **稀有/对抗性失败模式**：流水线评估典型生成行为，可能错过罕见或对抗性的失败案例。
3. **判别器噪声**：Discriminator 作为有噪声的模型依赖工具，其判别准确性会影响假设验证效力（附录 A.9 提供了消融分析）。
4. **计算成本**：成本随假设数量和验证测试规模线性扩展，最适合事后审计而非实时监控。
5. **非因果性**：验证的假设提供了统计支持的行为差异指示器，但不应解释为完整的因果解释。

## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [基准评估](../../concepts/benchmarking.html)
- [智能体](../../concepts/ai-agents.html)

---
*导入时间: 2026-05-07 06:01*
*来源: arXiv Daily Wiki Update 2026-05-07*
