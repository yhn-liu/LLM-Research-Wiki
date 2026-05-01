---
layout: concept
title: 医学AI
created: 2026-05-01
updated: 2026-05-01
type: concept
tags: [medical-ai, clinical, eeg, seizure-detection, healthcare]
papers:
  - 2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-
---

# 医学AI

## 定义

医学AI是将人工智能技术应用于医疗健康领域的研究方向，涵盖医学影像分析、临床辅助诊断、生物信号处理等。本库中有 1 篇论文探索了 LLM 在临床信号处理中的跨领域应用。

## 关键文献与发现

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
