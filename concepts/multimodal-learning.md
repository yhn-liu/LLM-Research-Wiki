---
layout: concept
title: 多模态学习
created: 2026-05-01
updated: 2026-05-01
type: concept
tags: [multimodal, vision-language, cross-modal, perception, reasoning]
papers:
  - 2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil
  - 2604-28196v1-hermes-toward-a-unified-driving-world-model-for-3d
---

# 多模态学习

## 定义

多模态学习是让模型同时处理和理解多种数据类型（如文本、图像、3D 点云）的 AI 研究方向。在 LLM 时代，多模态学习的核心挑战是如何将视觉感知与语言推理有效融合。本库中有 2 篇论文从训练方法和应用场景两个角度研究了这一问题。

## 关键文献与发现

### PRISM：多模态推理中的分布漂移

PRISM 发现多模态 LLM 训练中一个被忽视的问题：**感知错误和推理失败遵循不同的漂移模式**。标准 SFT→RLVR 流程中，这两类错误在 RL 阶段复合放大。

**技术方案**：设计 MoE 判别器，包含专门的感知专家和推理专家，从两个维度独立评估策略输出。这种解耦设计使纠正信号更精准——感知问题由感知专家反馈，推理问题由推理专家反馈。

**数据支撑**：从 Gemini 3 Flash 策划 11.3 万条高保真演示，包含密集视觉标注和逐步推理，聚焦最难问题。

📄 [查看论文](../papers/2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil.html)

### HERMES++：统一理解与生成的驾驶世界模型

HERMES++ 解决了多模态学习中的一个核心矛盾：**语义理解与物理预测的割裂**。现有驾驶世界模型要么侧重场景生成（忽略理解），要么侧重语义推理（无法预测几何演化）。

**统一框架**：通过 BEV 表示整合多视角信息，LLM 增强的世界查询促进理解分支的知识迁移，当前到未来的链接机制弥合时间差距。联合几何优化策略将显式几何约束与隐式正则化结合。

**关键结果**：在多个基准上同时实现强大的未来点云预测和 3D 场景理解，优于各自领域的专用方法。

📄 [查看论文](../papers/2604-28196v1-hermes-toward-a-unified-driving-world-model-for-3d.html)

## 研究趋势

两篇论文揭示了多模态学习的两个核心挑战：

1. **训练层面（PRISM）**：多模态推理中的错误模式比单模态更复杂，需要针对性的训练策略
2. **架构层面（HERMES++）**：理解和生成长期被视为不同任务，统一框架是新方向

**开放问题**：如何在保持感知准确性的同时提升推理深度？理解与生成的统一是否适用于更多场景？

## 相关论文

- [PRISM](../papers/2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil.html) — 多模态推理的分布对齐训练
- [HERMES++](../papers/2604-28196v1-hermes-toward-a-unified-driving-world-model-for-3d.html) — 统一 3D 场景理解与生成

## 相关概念

- [大语言模型](large-language-model.html) — 多模态学习的基础架构
- [世界模型](world-models.html) — 多模态生成的重要方向
- [知识蒸馏](knowledge-distillation.html) — 多模态模型的训练方法
- [自动驾驶](autonomous-driving.html) — 多模态学习的关键应用场景
