---
layout: paper
title: "AEGIS: A Holistic Benchmark for Evaluating Forensic Analysis of AI-Generated Academic Images"
created: 2026-05-01
updated: 2026-05-01
type: paper
arxiv_id: 2604.28177v1
authors: "Bo Zhang, Tzu-Yen Ma, Zichen Tang et al. (21 authors)"
published: 2026-04-30
categories: cs.CV, cs.CY
tags: [cv]
source_url: https://arxiv.org/abs/2604.28177v1
pdf_url: https://arxiv.org/pdf/2604.28177v1
confidence: high
status: analyzed
---

# AEGIS: A Holistic Benchmark for Evaluating Forensic Analysis of AI-Generated Academic Images

## 基本信息

- **arXiv ID:** [2604.28177v1](https://arxiv.org/abs/2604.28177v1)
- **作者:** Bo Zhang, Tzu-Yen Ma, Zichen Tang et al. (21 authors)
- **发布日期:** 2026-04-30
- **分类:** cs.CV, cs.CY

## 摘要

### English

We introduce AEGIS, A holistic benchmark for Evaluating forensic analysis of AI-Generated academic ImageS. Compared to existing benchmarks, AEGIS features three key advances: (1) Domain-Specific Complexity: covering seven academic categories with 39 fine-grained subtypes, exposing intrinsic forensic difficulty, where even GPT-5.1 reaches only 48.80% overall performance and expert models achieve only limited localization accuracy (IoU 30.09%); (2) Diverse Forgery Simulations: modeling four prevalent academic forgery strategies across 25 generative models, where 11 of which yield mean forensic accuracy below 50%, indicating forensics lags behind generation progress; (3) Multi-dimensional Forensic Evaluation: jointly evaluating detection, reasoning, and localization, revealing complementary strengths across model families—multimodal large language models (MLLMs) achieve 84.74% accuracy on textual artifact identification while expert detectors peak at 79.54% on binary authenticity detection. By evaluating 25 leading MLLMs, 9 expert models, and one unified multimodal understanding-and-generation model, AEGIS serves as a diagnostic testbed exposing fundamental limitations in academic image forensics.

### 中文

我们推出 AEGIS，这是一个评估人工智能生成的学术图像取证分析的整体基准。与现有基准相比，AEGIS 具有三个关键优势：（1）领域特定复杂性：涵盖 7 个学术类别，39 个细粒度子类型，暴露了固有的取证难度，即使 GPT-5.1 也能达到 48.80% 的整体性能，而专家模型仅实现有限的定位精度（IoU 30.09%）；(2) 多样化的伪造模拟：在 25 个生成模型中对四种流行的学术伪造策略进行建模，其中 11 个生成的平均取证准确度低于 50%，表明取证学落后于生成的进步；(3) 多维取证评估：联合评估检测、推理和定位，揭示模型家族之间的互补优势，多模态大语言模型 (MLLM) 在文本工件识别方面的准确率达到 84.74%，而专家检测器在二进制真实性检测方面的准确率峰值达到 79.54%。通过评估 25 个领先的 MLLM、9 个专家模型以及一个统一的多模态理解和生成模型，AEGIS 作为一个诊断测试台，暴露了学术图像取证的基本局限性。

## 核心贡献

- **构建领域特定基准 AEGIS**：首次针对学术领域构建 AI 生成图像取证基准，涵盖 7 个学术类别和 39 个细粒度子类型，暴露了学术图像取证的固有难度
- **多样化伪造策略模拟**：建模 4 种常见的学术伪造策略，使用 25 个不同的生成模型生成伪造图像，揭示取证检测能力落后于生成技术进步
- **多维评估框架**：联合评估检测（真伪判定）、推理（伪造类型识别）和定位（篡改区域标注）三个维度，揭示不同模型家族的互补优势
- **大规模模型评测**：系统评测了 25 个 MLLM、9 个专家模型和 1 个统一多模态理解生成模型，暴露当前学术图像取证的基本局限

## 方法概述

AEGIS 基准的设计围绕三个核心维度展开。首先是领域特定复杂性：选取学术场景中的 7 个类别（如实验图表、医学影像等），细分为 39 个子类型，模拟真实学术出版中可能出现的 AI 生成或篡改图像场景。这些图像具有领域特有的复杂结构（如科学图表、专业影像），比通用图像更难进行取证分析。

其次是多样化的伪造模拟：设计 4 种常见的学术伪造策略（如图像生成、局部篡改、数据伪造等），并使用 25 个不同的生成模型来创建伪造样本。这一设计确保了基准能覆盖不同生成技术和伪造手段，使得评测结果更具代表性和挑战性。

最后是多维取证评估：不同于以往仅关注二分类检测的基准，AEGIS 同时评估三个维度——检测（图像是否为 AI 生成）、推理（识别具体的伪造类型和手段）、定位（标注篡改或生成的区域），通过多维度联合评测揭示不同模型在各维度上的优势和不足。

## 实验结果

- **评测规模**: 25 个 MLLM + 9 个专家模型 + 1 个统一多模态模型
- **学术类别**: 7 大类，39 个细粒度子类型
- **伪造策略**: 4 种学术常见伪造策略，25 个生成模型
- **关键指标**:
  - GPT-5.1 整体性能仅 48.80%，说明学术图像取证难度极高
  - 专家模型定位精度 IoU 仅 30.09%
  - 11 个生成模型使取证准确度低于 50%，取证落后于生成
  - MLLM 在文本工件识别上达 84.74% 准确率
  - 专家检测器在二进制真实性检测上峰值 79.54%
- **核心发现**: MLLM 和专家模型在不同维度上具有互补优势，单一模型无法在所有维度上达到最优

## 相关概念

- [AI 生成图像检测](../concepts/ai-generated-image-detection.html)
- [图像取证](../concepts/image-forensics.html)
- [多模态大语言模型](../concepts/multimodal-llm.html)
- [对抗性评测](../concepts/adversarial-evaluation.html)
- [学术诚信](../concepts/academic-integrity.html)

---

*导入时间: 2026-05-01 19:53*
*来源: arXiv Daily Digest 2026-05-01*
