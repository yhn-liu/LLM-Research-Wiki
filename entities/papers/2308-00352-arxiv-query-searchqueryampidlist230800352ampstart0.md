---
layout: paper
title: "MetaGPT: Meta Programming for A Multi-Agent Collaborative Framework"
created: 2026-05-01
updated: 2026-05-01
type: paper
arxiv_id: 2308.00352
authors: "Sirui Hong, Mingchen Zhuge, Jiaqi Chen, Xiawu Zheng, Yuheng Cheng, Ceyao Zhang, Jinlin Wang, Zili Wang, Steven Ka Shing Yau, Zijuan Lin, Liyang Zhou, Chenyu Ran, Lingfeng Xiao, Chenglin Wu, Jürgen Schmidhuber"
published: 2026-05-01
categories: cs.AI, cs.MA, cs.AI
tags: [ai]
source_url: https://arxiv.org/abs/2308.00352
pdf_url: https://arxiv.org/pdf/2308.00352
source_type: url
confidence: high
status: analyzed
---

# MetaGPT: Meta Programming for A Multi-Agent Collaborative Framework

## 基本信息

- **arXiv ID:** [2308.00352](https://arxiv.org/abs/2308.00352)
- **作者:** Sirui Hong, Mingchen Zhuge, Jiaqi Chen, Xiawu Zheng, Yuheng Cheng, Ceyao Zhang, Jinlin Wang, Zili Wang, Steven Ka Shing Yau, Zijuan Lin, Liyang Zhou, Chenyu Ran, Lingfeng Xiao, Chenglin Wu, Jürgen Schmidhuber
- **分类:** cs.AI, cs.MA, cs.AI
- **导入类型:** url

## 摘要

Remarkable progress has been made on automated problem solving through societies of agents based on large language models (LLMs). Existing LLM-based multi-agent systems can already solve simple dialogue tasks. Solutions to more complex tasks, however, are complicated through logic inconsistencies due to cascading hallucinations caused by naively chaining LLMs. Here we introduce MetaGPT, an innovative meta-programming framework incorporating efficient human workflows into LLM-based multi-agent collaborations. MetaGPT encodes Standardized Operating Procedures (SOPs) into prompt sequences for more streamlined workflows, thus allowing agents with human-like domain expertise to verify intermediate results and reduce errors. MetaGPT utilizes an assembly line paradigm to assign diverse roles to various agents, efficiently breaking down complex tasks into subtasks involving many agents working together. On collaborative software engineering benchmarks, MetaGPT generates more coherent solutions than previous chat-based multi-agent systems. Our project can be found at https://github.com/geekan/MetaGPT

## 核心贡献

1. **元编程（Meta Programming）框架：** 提出了一种创新的元编程框架，将人类高效的工作流程（SOP，标准化操作流程）编码到 LLM 多智能体协作的提示序列中，使智能体能够按照结构化流程进行协作，而非简单地链式调用 LLM。

2. **SOP 编码机制：** 将软件工程等领域的标准化操作流程（SOP）转化为可执行的提示序列，使每个智能体具备类人的领域专业知识，并能在中间结果阶段进行验证和纠错，从源头上减少了级联幻觉（Cascading Hallucinations）问题。

3. **流水线（Assembly Line）范式：** 引入了类似工业流水线的协作范式，将复杂任务分解为多个子任务，分配给具有不同角色的专业智能体（如产品经理、架构师、工程师、测试员等）高效协作完成。

4. **中间结果验证机制：** 智能体在执行过程中会验证中间产出的质量，通过结构化的文档传递（如需求文档、设计文档、API 设计等）确保上下游智能体之间的信息一致性，有效抑制了幻觉传播。

5. **在软件工程基准上的优越性：** 在协作式软件工程基准测试中，MetaGPT 生成的解决方案比现有基于聊天的多智能体系统更加连贯和可靠。

## 方法概述

MetaGPT 的核心方法包括以下几个关键组件：

- **角色专业化分工：** 系统定义了完整的软件开发团队角色，包括产品经理（Product Manager）、架构师（Architect）、工程师（Engineer）、项目经理（Project Manager）和测试工程师（QA Engineer）等，每个角色具有明确的职责和输出规范。

- **SOP 驱动的提示序列：** 将人类软件开发的标准流程编码为结构化的提示序列。每个角色在执行任务时遵循预定义的 SOP，确保工作流程的规范性和可预测性。例如，产品经理先输出 PRD 文档，架构师基于 PRD 输出系统设计，工程师基于设计文档编写代码。

- **结构化文档传递：** 各智能体之间通过结构化的中间文档进行信息传递（而非自由对话），如产品需求文档（PRD）、系统设计文档、API 接口文档、测试计划等。这些文档作为下游智能体的输入，确保信息传递的准确性和一致性。

- **中间结果验证与纠错：** 每个智能体在接收上游输出后，会对其进行验证和审查，发现问题时可以反馈给上游进行修正。这种机制有效减少了级联幻觉——即一个智能体的错误被后续智能体放大和传播的现象。

- **流水线式任务分解：** 复杂任务被分解为按顺序执行的子任务，形成清晰的流水线。每个阶段有明确的输入、输出和质量标准，类似于工业生产中的流水线模式。

- **可执行代码生成：** 最终输出不仅是对话文本，而是可执行的代码项目，包括完整的代码结构、文档和测试。

## 实验结果

MetaGPT 在多个软件工程基准测试上进行了评估：

- **代码生成质量：** MetaGPT 生成的代码在可运行性、完整性和可维护性方面优于现有的基于聊天的多智能体系统（如 ChatDev 等），生成了更加连贯和可靠的软件解决方案。

- **级联幻觉抑制：** 与简单链式 LLM 调用相比，MetaGPT 的 SOP 编码和中间验证机制显著减少了级联幻觉的发生率，提高了整体任务完成的准确性。

- **复杂任务处理能力：** 在处理较复杂的软件工程任务时，MetaGPT 的流水线范式展现出明显优势，能够有效分解和协调多智能体的工作，产出质量更高的解决方案。

- **协作效率：** 相比纯对话式协作，结构化的文档传递和角色分工使协作更加高效，减少了不必要的对话轮次和信息损失。

- **可扩展性：** 框架展示了良好的可扩展性，能够根据任务复杂度灵活调整角色数量和流水线深度，适用于不同规模的软件工程项目。

## 相关论文

<!-- 待填充：添加相关论文链接 -->

## 相关概念

- [智能体](../../concepts/ai-agents.html)
- [大语言模型](../../concepts/large-language-model.html)

---
*导入时间: 2026-05-01 23:30*
*导入方式: url*
