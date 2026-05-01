---
layout: concept
title: 世界模型
created: 2026-05-01
updated: 2026-05-01
type: concept
tags: [world-model, prediction, generation, 3D, driving]
papers:
  - 2604-28196v1-hermes-toward-a-unified-driving-world-model-for-3d
---

# 世界模型

## 定义

世界模型是能够学习环境动态规律、预测未来状态的计算模型。在 AI 领域，世界模型旨在让智能体通过内部模拟理解世界运行规律，用于规划、决策和生成。本库中有 1 篇论文推动了驾驶场景世界模型的前沿。

## 关键文献与发现

### HERMES++：统一理解与生成的驾驶世界模型

HERMES++ 针对驾驶世界模型的核心矛盾：现有方法**要么侧重场景生成**（如视频扩散模型），**要么侧重语义理解**（如 LLM 推理），两者在同一框架中难以兼顾。

**统一方案**：将 3D 场景理解和未来几何预测集成在一个框架内。通过四个关键设计实现统一：
- BEV 表示将多视角空间信息整合到 LLM 兼容的结构中
- LLM 增强的世界查询促进理解分支的知识迁移
- 当前到未来的链接机制弥合时间差距，根据语义上下文调节几何演化
- 联合几何优化策略结合显式几何约束与隐式正则化

**关键结果**：在多个基准上同时实现强大的未来点云预测和 3D 场景理解性能，均优于各自领域的专用方法。模型和代码已开源。

📄 [查看论文](../papers/2604-28196v1-hermes-toward-a-unified-driving-world-model-for-3d.html)

## 研究趋势

HERMES++ 代表了世界模型从"纯生成"向"理解+生成统一"的转变：

- **传统路径**：生成逼真的未来帧（如 Sora 风格的视频生成）
- **新路径**：同时理解环境动态和预测未来状态（HERMES++）
- **关键洞察**：语义理解和几何预测不是互斥的，可以相互增强

**开放问题**：统一框架能否扩展到更复杂的城市场景？计算效率如何进一步提升？

## 相关论文

- [HERMES++](../papers/2604-28196v1-hermes-toward-a-unified-driving-world-model-for-3d.html) — 统一 3D 场景理解与未来几何预测

## 相关概念

- [多模态学习](multimodal-learning.html) — 世界模型需要处理多种模态的输入输出
- [自动驾驶](autonomous-driving.html) — 世界模型在驾驶场景中的重要应用
- [大语言模型](large-language-model.html) — LLM 作为世界模型的语义组件
- [智能体](ai-agents.html) — 智能体利用世界模型进行规划和决策
