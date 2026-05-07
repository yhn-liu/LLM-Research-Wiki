---
layout: concept
title: 医学AI
created: 2026-05-01
updated: 2026-05-07
type: concept
tags: [medical-ai, clinical, eeg, seizure-detection, healthcare]
papers:
  - 2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-
---

# 医学AI

## 定义

医学AI是将人工智能技术应用于医疗健康领域的研究方向，涵盖医学影像分析、临床辅助诊断、生物信号处理等。本库中有 1 篇论文探索了 LLM 在临床信号处理中的跨领域应用。

## 关键文献与发现

- [Beyond Semantics: An Evidential Reasoning-Aware Multi-View Learning Framework for Trustworthy Mental Health Prediction](../entities/papers/2605-05121v1-beyond-semantics-an-evidential-reasoning-aware-mul.html)（2026-05-06）：使用文本数据进行的自动心理健康预测通过深度学习和大型语言模型显示出了有希望的结果。

- [EQUITRIAGE: A Fairness Audit of Gender Bias in LLM-Based Emergency Department Triage](../entities/papers/2605-03998v1-equitriage-a-fairness-audit-of-gender-bias-in-llm.html)（2026-05-05）：急诊科分诊为患者分配一个视力评分，以确定治疗的优先顺序，临床证据记录了人类视力评估中持续存在的性别差异。

- [Safety and accuracy follow different scaling laws in clinical large language models](../entities/papers/2605-04039v1-safety-and-accuracy-follow-different-scaling-laws.html)（2026-05-05）：临床法学硕士通常通过增加模型大小、上下文长度、检索复杂性或推理时间计算来扩展，隐含的期望是更高的准确性意味着更安全的行为。

- [Foundation Models to Unlock Real-World Evidence from Nationwide Medical Claims](../entities/papers/2605-02740v1-foundation-models-to-unlock-real-world-evidence-fr.html)（2026-05-04）：来自大规模现实世界数据 (RWD) 的证据越来越多地为监管评估和医疗保健决策提供信息。

- [When Audio-Language Models Fail to Leverage Multimodal Context for Dysarthric Speech Recognition](../entities/papers/2605-02782v1-when-audio-language-models-fail-to-leverage-multim.html)（2026-05-04）：自动语音识别（ASR）系统对于构音障碍和其他非典型语音仍然很脆弱。

### LLM as Clinical Graph Structure Refiner

**问题**：EEG（脑电图）信号固有的噪声使得癫痫检测的图表示学习面临挑战。现有图构建方法（基于相关性或学习的）因 EEG 噪声常产生冗余或不相关边，损害图表示质量。

**方案**：提出两阶段框架，创新性地将 LLM 用作图边缘细化器。第一阶段用 Transformer+MLP 构建初始图结构，第二阶段利用 LLM 的推理和上下文理解能力优化边连接，过滤冗余边、增强关键连接。

**关键发现**：在 TUSZ 数据集上验证了框架有效性，展示了 LLM 跨领域应用于医学信号处理的潜力——LLM 不仅能处理文本，还能辅助优化医学数据的结构化表示。

📄 [查看论文](../entities/papers/2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-.html)

## 研究趋势

这篇论文揭示了一个有趣的方向：**LLM 的能力正在超越传统 NLP 任务**。通过将 LLM 的推理能力与图神经网络结合，可以解决医学信号处理中的结构优化问题。这种跨领域的"LLM as X"范式可能在更多医学场景中发挥作用。

## 相关论文

- [Clinical Graph Refiner](../entities/papers/2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-.html) — LLM 优化 EEG 图结构用于癫痫检测

## 相关概念

- [大语言模型](large-language-model.html) — LLM 作为临床工具的核心技术
- [图神经网络](graph-neural-networks.html) — 医学数据的图结构学习方法
