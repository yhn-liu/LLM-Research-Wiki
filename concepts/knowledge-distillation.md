---
layout: concept
title: 知识蒸馏
created: 2026-05-01
updated: 2026-05-01
type: concept
tags: [distillation, teacher-student, model-compression, black-box, policy-distillation]
papers:
  - 2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil
---

# 知识蒸馏

## 定义

知识蒸馏（Knowledge Distillation）是一种模型压缩技术，通过将大型教师模型（teacher model）的知识迁移到小型学生模型（student model）中，使学生模型在保持较小规模的同时获得接近教师模型的性能。其核心思想是利用教师模型的软标签（soft labels）或中间表示来指导学生模型的学习，而不仅仅是使用硬标签（hard labels）。在大语言模型时代，知识蒸馏已成为模型部署和能力迁移的关键技术。

## 发展脉络

### 基础理论（2006–2015）
- **2006**：Caruana 等人首次提出模型压缩的概念，通过训练小型网络模拟大型集成模型
- **2014**：Hinton 等人正式提出知识蒸馏框架，定义了温度缩放的软标签和蒸馏损失函数
- **2015**：FitNets 提出通过学习中间层表示（hints）进行更深的蒸馏

### 白箱蒸馏发展（2016–2020）
- **2016**：Attention Transfer 提出注意力蒸馏方法，迁移教师模型的注意力分布
- **2017**：Crépeau 等人提出特征蒸馏，对齐教师和学生模型的中间层表示
- **2018**：PKD（Patient Knowledge Distillation）提出逐层知识迁移
- **2019**：TinyBERT 等工作探索了 Transformer 架构的专项蒸馏方法

### 黑箱蒸馏兴起（2020–2024）
- **2020**：研究者发现仅通过教师模型的输出概率分布即可进行有效蒸馏
- **2021**：Black-box distillation 方法在 NLP 任务中取得与白箱蒸馏相近的效果
- **2022**：ChatGPT 的发布引发了通过 API 输出进行知识蒸馏的热潮
- **2023**：Alpaca、Vicuna 等开源模型展示了黑箱蒸馏在 LLM 中的应用

### 在线策略蒸馏（2024–2026）
- **2024**：Online Policy Distillation（OPD）方法提出，解决了离线蒸馏中分布偏移的问题
- **2025**：PRISM 提出黑箱在线策略蒸馏（Black-box OPD），在不访问模型权重的情况下进行高效蒸馏
- **2026**：多模态场景下的蒸馏方法开始出现，将视觉和语言知识统一迁移

## 核心技术/方法

### 蒸馏范式
- **白箱蒸馏**：访问教师模型的完整权重和中间表示，进行深层知识迁移
- **黑箱蒸馏**：仅通过教师模型的 API 输出（概率分布或文本）进行蒸馏
- **在线蒸馏**：教师和学生同时训练，动态更新知识
- **离线蒸馏**：先训练教师模型，再用其输出训练学生模型

### 蒸馏目标
- **logit 蒸馏**：匹配教师和学生模型的输出概率分布
- **特征蒸馏**：对齐中间层的特征表示
- **关系蒸馏**：保持样本间关系结构的一致性
- **策略蒸馏**：在强化学习中迁移教师的决策策略

### 在线策略蒸馏（OPD）
- **核心思想**：学生模型在自身策略分布上采样，并从教师模型获取相应反馈
- **解决的问题**：避免离线蒸馏中的分布偏移（distribution shift）
- **黑箱 OPD**：PRISM 提出的无需访问教师权重的在线策略蒸馏方法

### 多模态蒸馏
- **跨模态知识迁移**：将多模态教师的知识迁移到单模态学生
- **感知-推理分离**：分别蒸馏视觉感知和推理能力
- **统一蒸馏框架**：同时处理多种模态的知识迁移

## 开放问题与挑战

1. **蒸馏税**：学生模型在蒸馏后可能出现能力退化（distillation tax），如何最小化性能损失是关键问题
2. **分布偏移**：离线蒸馏中，学生模型的分布与教师模型的训练分布不匹配
3. **可扩展性**：对于超大模型，完全蒸馏所有知识的计算成本依然很高
4. **评估标准**：如何全面评估蒸馏后模型的能力保持程度仍缺乏统一标准
5. **安全性**：蒸馏可能转移教师模型的安全对齐问题，如何保证蒸馏后的安全性
6. **多任务蒸馏**：同时从多个教师模型蒸馏不同能力的挑战
7. **法律与伦理**：通过 API 输出蒸馏商业模型可能涉及知识产权问题

## 相关论文

- [PRISM: Pre-alignment via Black-box On-policy Distillation for Multimodal Reinforcement Learning](../papers/2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil.html) — 提出黑箱在线策略蒸馏（Black-box OPD），在多模态强化学习中实现无需访问权重的高效知识迁移和预对齐

## 相关概念

- [大语言模型](large-language-model.md.html) — 知识蒸馏的主要应用对象
- [强化学习](reinforcement-learning.md.html) — 策略蒸馏是强化学习中的重要技术
- [多模态学习](multimodal-learning.md.html) — 多模态场景下的蒸馏应用
- [AI安全与对齐](ai-safety-alignment.md.html) — 蒸馏过程中的安全对齐问题
