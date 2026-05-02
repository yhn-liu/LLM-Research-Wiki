---
layout: paper
title: "CAMEL: Communicative Agents for \"Mind\" Exploration of Large Language Model Society"
created: 2026-05-01
updated: 2026-05-01
type: paper
arxiv_id: 2303.17760
authors: "Guohao Li, Hasan Abed Al Kader Hammoud, Hani Itani, Dmitrii Khizbullin, Bernard Ghanem"
published: 2026-05-01
categories: cs.AI, cs.CL, cs.CY
tags: [nlp, ai]
source_url: https://arxiv.org/abs/2303.17760
pdf_url: https://arxiv.org/pdf/2303.17760
source_type: url
confidence: high
status: analyzed
---

# CAMEL: Communicative Agents for "Mind" Exploration of Large Language Model Society

## 基本信息

- **arXiv ID:** [2303.17760](https://arxiv.org/abs/2303.17760)
- **作者:** Guohao Li, Hasan Abed Al Kader Hammoud, Hani Itani, Dmitrii Khizbullin, Bernard Ghanem
- **分类:** cs.AI, cs.CL, cs.CY
- **导入类型:** url

## 摘要

The rapid advancement of chat-based language models has led to remarkable progress in complex task-solving. However, their success heavily relies on human input to guide the conversation, which can be challenging and time-consuming. This paper explores the potential of building scalable techniques to facilitate autonomous cooperation among communicative agents, and provides insight into their "cognitive" processes. To address the challenges of achieving autonomous cooperation, we propose a novel communicative agent framework named role-playing. Our approach involves using inception prompting to guide chat agents toward task completion while maintaining consistency with human intentions. We showcase how role-playing can be used to generate conversational data for studying the behaviors and capabilities of a society of agents, providing a valuable resource for investigating conversational language models. In particular, we conduct comprehensive studies on instruction-following cooperation in multi-agent settings. Our contributions include introducing a novel communicative agent framework, offering a scalable approach for studying the cooperative behaviors and capabilities of multi-agent systems, and open-sourcing our library to support research on communicative agents and beyond: https://github.com/camel-ai/camel.

## 核心贡献

1. **提出角色扮演框架（Role-Playing）：** 首次提出了一种基于角色扮演的通信智能体框架，使两个 LLM 智能体能够在无需人工干预的情况下自主协作完成复杂任务。每个智能体被赋予特定角色（如 AI 研发员、产品经理等），并通过角色约束保持行为一致性。

2. **Inception Prompting 技术：** 设计了一种"始发提示"（Inception Prompting）机制，通过精心构造的初始提示词引导智能体之间的对话走向，使其在保持人类意图一致性的同时自主推进任务完成。这是实现自主多智能体协作的关键技术。

3. **可扩展的多智能体协作研究范式：** 提出了一种可扩展的方法来研究多智能体系统的协作行为和能力，能够生成大量对话数据用于分析智能体的"认知"过程，为研究 LLM 社会行为提供了宝贵的资源和工具。

4. **开源框架与工具：** 开源了 CAMEL 库（https://github.com/camel-ai/camel），支持通信智能体及相关研究，降低了多智能体协作研究的门槛。

## 方法概述

CAMEL 的核心方法是**角色扮演（Role-Playing）**框架，其工作流程如下：

- **角色分配：** 系统为两个智能体分别分配互补的角色（例如"AI 研发员"和"产品经理"），每个角色附带详细的能力描述和行为约束。
- **Inception Prompting 引导机制：** 通过构造包含任务描述、角色定义和交互规则的初始提示词（Inception Prompt），引导两个智能体自主开展多轮对话。该提示词不仅定义了任务目标，还规定了对话的终止条件。
- **自主对话协作：** 两个智能体基于角色设定，通过交替发言的方式进行多轮协作对话。一个智能体提出请求（User Agent），另一个智能体提供响应（Assistant Agent），双方在角色约束下共同推进任务。
- **指令遵循式合作：** 在多智能体环境中研究指令遵循式合作（Instruction-following Cooperation），探索智能体如何在保持角色一致性的同时理解和执行复杂指令。
- **对话数据生成：** 通过角色扮演框架生成大量多智能体对话数据，可用于分析智能体的行为模式、协作能力和"认知"过程。

该方法的核心优势在于利用 LLM 的指令遵循能力和角色扮演约束，实现了无需人工干预的自主多智能体协作。

## 实验结果

CAMEL 在多个维度上进行了全面的实验评估：

- **任务完成能力：** 在角色扮演框架下，两个 LLM 智能体能够自主协作完成多种复杂任务，包括编写程序、创建游戏、进行科学研究等。实验表明 inception prompting 能有效引导对话走向预期目标。
- **角色一致性验证：** 实验验证了角色扮演约束的有效性，智能体在对话过程中能够较好地保持其角色设定，展现出与角色一致的专业能力和行为模式。
- **多智能体协作分析：** 通过生成的对话数据，深入分析了多智能体协作中的行为模式，包括任务分配、信息交换和冲突解决等机制，揭示了 LLM 智能体社会中的"认知"过程。
- **指令遵循评估：** 在指令遵循式合作实验中，评估了智能体在不同复杂度任务下的表现，验证了框架在处理多样化任务时的鲁棒性和适应性。
- **可扩展性验证：** 展示了框架在不同任务类型和复杂度下的可扩展性，证明了该方法可以广泛应用于各种多智能体协作场景。

## 相关论文

<!-- 待填充：添加相关论文链接 -->

## 相关概念

- [智能体](../../concepts/ai-agents.html)
- [大语言模型](../../concepts/large-language-model.html)


## 分析信息

- **分析来源:** pdf_analysis
- **分析置信度:** high
- **分析时间:** 2026-05-02 06:02
- **关键词:** LLM, PPO, fine-tuning, generation
- **PDF 路径:** /root/wiki/raw/papers/2303-17760.pdf

---
*导入时间: 2026-05-01 23:30*
*导入方式: url*
