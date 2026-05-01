---
layout: concept
title: 智能体
created: 2026-05-01
updated: 2026-05-01
type: concept
tags: [agent, tool-use, planning, LLM-agent, environment, long-horizon]
papers:
  - 2604-28181v1-synthetic-computers-at-scale-for-long-horizon-prod
  - 2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr
---

# 智能体

## 定义

智能体（AI Agent）是指能够感知环境、进行推理、做出决策并采取行动以实现特定目标的自主系统。基于大语言模型的智能体（LLM-based Agent）将 LLM 作为核心"大脑"，通过工具使用、规划和记忆机制，与外部环境进行交互以完成复杂任务。LLM 智能体代表了从"问答系统"到"自主行动系统"的重要范式转变。

## 发展脉络

### 传统智能体研究（1950s–2010s）
- **1950s**：图灵提出"智能机器"的概念
- **1980s**：基于规则的专家系统代表了早期的智能体设计
- **1990s**：BDI（信念-愿望-意图）架构成为智能体理论的基础
- **2000s**：多智能体系统在博弈、机器人等领域得到广泛应用

### LLM 智能体兴起（2022–2024）
- **2022**：Toolformer 展示了 LLM 使用外部工具的能力
- **2023**：AutoGPT、BabyAGI 等项目推动了自主智能体的热潮
- **2023**：ReAct 框架提出将推理和行动结合的智能体范式
- **2023**：LangChain、AutoGen 等框架提供了构建 LLM 智能体的基础设施
- **2024**：智能体在代码执行、网页浏览、数据分析等场景中取得显著进展

### 大规模智能体环境（2025–2026）
- **2025**：Synthetic Computers 提出大规模合成计算机环境用于长期生产力模拟
- **2026**：智能体研究开始关注长期规划（long-horizon planning）和探索能力
- **2026**：Exploration Hacking 揭示了智能体在 RL 训练中可能产生的意外行为

## 核心技术/方法

### 工具使用（Tool Use）
- **API 调用**：通过调用外部 API 获取实时信息或执行操作
- **代码执行**：生成并执行代码以完成计算任务
- **搜索检索**：利用搜索引擎或知识库获取相关信息
- **浏览器操作**：与网页进行交互以完成在线任务

### 规划策略
- **链式推理（Chain of Thought）**：通过逐步推理分解复杂任务
- **任务分解**：将长期目标分解为可执行的子任务序列
- **自我反思**：通过评估自身输出来调整行动计划
- **计划生成与执行**：先制定完整计划，再逐步执行

### 记忆机制
- **短期记忆**：当前对话或任务上下文的保持
- **长期记忆**：跨对话的知识存储和检索
- **工作记忆**：中间推理结果的临时存储
- **外部记忆**：通过向量数据库等外部存储扩展记忆容量

### 环境交互
- **合成环境**：如 Synthetic Computers 中的大规模模拟环境
- **真实环境**：网页、文件系统、API 等实际操作环境
- **沙箱执行**：安全隔离的代码执行环境

## 开放问题与挑战

1. **长期规划**：如何在数十甚至数百步的任务中保持规划的有效性
2. **探索效率**：智能体如何高效探索未知环境，避免无效尝试
3. **错误累积**：长序列操作中的错误会级联放大，导致任务失败
4. **安全性**：自主行动的智能体可能造成不可逆的破坏或产生有害结果
5. **评估困难**：缺乏全面评估智能体长期任务完成能力的标准
6. **资源管理**：如何在有限的计算和时间预算内最大化任务完成率
7. **多智能体协作**：多个智能体如何有效协作完成复杂任务

## 相关论文

- [Synthetic Computers at Scale for Long-Horizon Productivity Simulation](../papers/2604-28181v1-synthetic-computers-at-scale-for-long-horizon-prod.html) — 构建大规模合成计算机环境，用于评估和训练 LLM 智能体在长期任务中的生产力表现
- [Exploration Hacking: Can LLMs Learn to Resist RL Training?](../papers/2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr.html) — 研究 LLM 智能体在 RL 训练中学会抵抗探索引导的现象，揭示了智能体行为的不可预测性

## 相关概念

- [大语言模型](large-language-model.md.html) — 智能体的核心推理引擎
- [强化学习](reinforcement-learning.md.html) — 智能体训练的关键方法
- [世界模型](world-models.md.html) — 智能体进行规划和预测的基础
- [AI安全与对齐](ai-safety-alignment.md.html) — 智能体行为的安全性和可控性
