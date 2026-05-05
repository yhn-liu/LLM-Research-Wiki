---
layout: paper
title: "When Audio-Language Models Fail to Leverage Multimodal Context for Dysarthric Speech Recognition"
created: 2026-05-05
updated: 2026-05-05
type: paper
arxiv_id: 2605.02782v1
authors: "Pehuén Moure, Niclas Pokel, Bilal Bounajma, Yingqiang Gao, Roman Boehringer, Longbiao Cheng, Shih-Chii Liu"
published: 2026-05-04
categories: cs.AI, cs.CL, eess.AS
tags: [ai, nlp, benchmark]
source_url: https://arxiv.org/abs/2605.02782v1
pdf_url: https://arxiv.org/pdf/2605.02782v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: []
---

# When Audio-Language Models Fail to Leverage Multimodal Context for Dysarthric Speech Recognition

## 基本信息

- **arXiv ID:** [2605.02782v1](https://arxiv.org/abs/2605.02782v1)
- **作者:** Pehuén Moure, Niclas Pokel, Bilal Bounajma et al.
- **发布日期:** 2026-05-04
- **分类:** cs.AI, cs.CL, eess.AS
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2605.02782v1)


## 摘要

### English

Automatic speech recognition (ASR) systems remain brittle on dysarthric and other atypical speech. Recent audio-language models raise the possibility of improving performance by conditioning on additional clinical context at inference time, but it is unclear whether these models can make use of such information. We introduce a benchmark built on the Speech Accessibility Project (SAP) dataset that tests whether diagnosis labels, clinician-derived speech ratings, and progressively richer clinical descriptions improve transcription accuracy for dysarthric speech. Across matched comparisons on nine models, we find that current models do not meaningfully use this context: diagnosis-informed and clinically detailed prompts yield negligible improvements and often degrade word error rate. We complement the prompting analysis with context-dependent fine-tuning, showing that LoRA adaptation with a mixture of clinical prompt formats achieves a WER of 0.066, a 52% relative reduction over the frozen baseline, while preserving performance when context is unavailable. Subgroup analyses reveal significant gains for Down syndrome and mild-severity speakers. These results clarify where current models fall short and provide a testbed for measuring progress toward more inclusive ASR.

### 中文

自动语音识别系统对构音障碍和其他非典型语音仍很脆弱。最近的音频语言模型提供了通过在推理时附加临床上下文来提高性能的可能性，但这些模型能否利用此类信息尚不明确。我们基于语音无障碍项目（SAP）数据集构建了一个基准，测试诊断标签、临床医生评定的语音评分以及渐进丰富的临床描述是否能提高构音障碍语音的转录准确性。在 9 个模型的匹配比较中，我们发现当前模型没有有意义地利用这些上下文：诊断信息和临床详细提示带来的改进微乎其微，且经常降低词错误率。我们通过上下文相关微调补充了提示分析，表明使用混合临床提示格式的 LoRA 微调实现了 0.066 的 WER，相对冻结基线降低了 52%，同时在上下文不可用时保持性能。亚组分析显示唐氏综合征和轻度严重程度说话者获得了显著收益。这些结果阐明了当前模型的不足，并为衡量更具包容性的 ASR 进展提供了测试平台。

## 核心贡献

1. **首次系统评估音频语言模型的临床上下文利用能力**：对 9 个音频语言模型（包括 Qwen3-Omni、Gemma-4、Whisper、Voxtral 等）在构音障碍语音上进行系统评估，发现冻结模型无一能有效利用临床上下文。
2. **三种失败模式识别**：归纳出鲁棒型（WER 不随上下文变化）、退化型（WER 随上下文增加而上升）和格式依赖型（仅特定上下文格式有用）。
3. **上下文相关微调的有效性证明**：尽管冻结模型无法利用上下文，但 LoRA 微调可让模型学会利用临床信息，实现 WER 0.066（SOTA），表明模型失败源于训练数据缺乏而非根本性限制。
4. **亚组分析**：揭示了唐氏综合征和轻度构音障碍说话者的显著改善，为针对性系统优化提供了方向。

## 方法概述

实验分为两个主要部分：

**提示评估（Prompting Evaluation）**：设计 11 种逐渐增加临床信息的提示条件——从零上下文控制、仅有诊断标签、语音评分、简洁临床描述、完整临床描述到跟进修正。在 9 个模型上对 SAP 数据集的 11,218 个匹配样本进行评估。评估指标为 WER（词错误率）、CER（字符错误率）和 SemScore。

**上下文相关微调（Context-Dependent Fine-Tuning）**：选择在提示评估中表现良好的 Qwen3-ASR-1.7B 作为基座，使用 LoRA 对混合临床提示格式（随机化提示以强制模型学习上下文利用）进行微调，随后在 5 种上下文条件下评估（零上下文到完整临床描述）。

## 实验结果

- **冻结模型全面失败**：所有 9 个冻结模型在添加临床上下文后均未显示有意义的 WER 改善；多数模型 WER 的上下文变动不超过 0.02。
- **三种失败模式**：Whisper、Cohere 等为鲁棒型；Gemma-4、Qwen2-Audio 为退化型；Audio Flamingo 3 为格式依赖型（随上下文增加停止幻觉而非真正改善）。
- **LoRA 微调效果**：Qwen3-ASR-1.7B 经 LoRA 微调后 WER 从基线的 ~0.138 降至 0.066（相对降低 52%），并在零上下文条件下保持其原始性能。
- **亚组收益**：唐氏综合征亚组（最大改善）和轻度严重程度亚组收益最为显著。
- **Wav2Vec2 和传统 ASR**：专门的 ASR 系统（Whisper-large-v3: 0.171 WER）优于通用音频语言模型（Gemma-4-4B: 0.311 WER）。

## 局限性与注意点

- **单数据集评估**：仅基于 SAP 数据集，其他构音障碍语料库（如 TORGO、UA-Speech）上的表现未知。
- **SAP 数据多样性**：SAP 数据集覆盖的构音障碍类型和严重程度可能存在选择偏差。
- **API 模型不稳定**：商业 API 模型（GPT-4o、Gemini 等）的结果可能随时间变化（模型版本更新）。
- **LoRA 微调范围有限**：仅在 Qwen3-ASR-1.7B 上验证了微调方法，其他模型架构的适用性未测试。
- **临床上下文简化为文本**：未利用更丰富的临床信号（如声学特征、发音器官运动数据）。

## 相关概念（详细）

- **构音障碍语音识别 (Dysarthric ASR)**：针对运动性言语障碍的语音识别，是 ASR 领域的重要公平性挑战。本文证实冻结音频语言模型在此任务上无法利用临床上下文。
- **音频语言模型 (Audio-Language Models)**：原生处理音频输入的多模态 LLM（如 Qwen3-Omni、Gemma-4）。本文首次对它们进行系统化的临床上下文条件评估。
- **LoRA 微调**：低秩适配方法。本文证明 LoRA 微调可以教会模型利用临床上下文，而冻结模型则不行——这表明问题在于训练数据分布而非模型架构。

## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [多模态学习](../../concepts/multimodal-learning.html)
- [基准评估](../../concepts/benchmarking.html)
- [医学AI](../../concepts/medical-ai.html)

---
*导入时间: 2026-05-05 06:01*
*来源: arXiv Daily Wiki Update 2026-05-05*
