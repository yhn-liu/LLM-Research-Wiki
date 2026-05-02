---
layout: paper
title: "ChatDev: Communicative Agents for Software Development"
created: 2026-05-01
updated: 2026-05-01
type: paper
arxiv_id: 2307.07924
authors: "Chen Qian, Wei Liu, Hongzhang Liu, Nuo Chen, Yufan Dang, Jiahao Li, Cheng Yang, Weize Chen, Yusheng Su, Xin Cong, Juyuan Xu, Dahai Li, Zhiyuan Liu, Maosong Sun"
published: 2026-05-01
categories: cs.SE, cs.CL, cs.MA
tags: [nlp]
source_url: https://arxiv.org/abs/2307.07924
pdf_url: https://arxiv.org/pdf/2307.07924
source_type: url
confidence: high
status: analyzed
---

# ChatDev: Communicative Agents for Software Development

## 基本信息

- **arXiv ID:** [2307.07924](https://arxiv.org/abs/2307.07924)
- **作者:** Chen Qian, Wei Liu, Hongzhang Liu, Nuo Chen, Yufan Dang, Jiahao Li, Cheng Yang, Weize Chen, Yusheng Su, Xin Cong, Juyuan Xu, Dahai Li, Zhiyuan Liu, Maosong Sun
- **分类:** cs.SE, cs.CL, cs.MA
- **导入类型:** url

## 摘要

Software development is a complex task that necessitates cooperation among multiple members with diverse skills. Numerous studies used deep learning to improve specific phases in a waterfall model, such as design, coding, and testing. However, the deep learning model in each phase requires unique designs, leading to technical inconsistencies across various phases, which results in a fragmented and ineffective development process. In this paper, we introduce ChatDev, a chat-powered software development framework in which specialized agents driven by large language models (LLMs) are guided in what to communicate (via chat chain) and how to communicate (via communicative dehallucination). These agents actively contribute to the design, coding, and testing phases through unified language-based communication, with solutions derived from their multi-turn dialogues. We found their utilization of natural language is advantageous for system design, and communicating in programming language proves helpful in debugging. This paradigm demonstrates how linguistic communication facilitates multi-agent collaboration, establishing language as a unifying bridge for autonomous task-solving among LLM agents. The code and data are available at https://github.com/OpenBMB/ChatDev.

## 核心贡献

1. **聊天驱动的软件开发框架：** 提出了 ChatDev，一个基于对话（Chat-powered）的多智能体软件开发框架，将软件开发过程中的设计、编码和测试等阶段统一到 LLM 驱动的对话范式中，解决了传统方法在各阶段技术不一致导致的碎片化问题。

2. **Chat Chain 机制：** 设计了 Chat Chain（聊天链）机制，将复杂的软件开发任务分解为一系列结构化的对话阶段，指导智能体在每个阶段应该交流什么内容。该机制以瀑布模型为灵感，将软件生命周期划分为设计、编码、测试、文档等子阶段。

3. **通信去幻觉（Communicative Dehallucination）：** 提出了通信去幻觉技术，指导智能体如何进行有效沟通，减少 LLM 在对话中产生的幻觉问题。通过结构化的对话约束和角色提示，提高对话质量和任务完成的准确性。

4. **语言作为统一桥梁：** 验证了自然语言在系统设计阶段的优势，以及编程语言在调试阶段的有效性，证明了语言通信可以作为 LLM 智能体自主协作解决复杂任务的统一桥梁。

5. **端到端软件开发能力：** 实现了从需求分析到代码生成的完整软件开发流程，展示了多智能体协作在实际软件工程任务中的可行性。

## 方法概述

ChatDev 的核心架构包含以下关键组件：

- **角色分配：** 系统定义了多种软件开发角色，包括 CEO（需求确认）、CTO（技术设计）、程序员（代码编写）、测试员（测试验证）等，每个角色由一个 LLM 智能体扮演。

- **Chat Chain（聊天链）：** 将软件开发流程组织为一个由多个对话阶段组成的链条。每个阶段包含特定的目标和参与角色，例如：
  - 阶段1：CEO 与用户确认需求
  - 阶段2：CEO 与 CTO 讨论设计方案
  - 阶段3：CTO 与程序员协作编写代码
  - 阶段4：程序员与测试员进行测试和调试
  - 每个阶段的对话历史作为下一阶段的上下文输入。

- **Communicative Dehallucination（通信去幻觉）：** 通过精心设计的角色提示（Role Prompting）和对话模板，约束智能体的输出，使其在软件开发语境中保持专业性和准确性。该技术减少了 LLM 在代码生成和设计讨论中产生幻觉的可能性。

- **瀑布模型启发的工作流：** 整体工作流程借鉴了传统软件工程的瀑布模型，但通过自然语言对话实现各阶段的衔接，使得不同技能的智能体能够通过统一的通信接口协作。

- **多轮对话驱动：** 每个开发阶段通过多轮对话完成，智能体之间通过自然语言或编程语言进行交流，最终生成完整的软件项目。

## 实验结果

ChatDev 在软件工程基准测试上进行了全面评估：

- **软件项目生成：** ChatDev 能够自动生成完整的小型软件项目，包括设计文档、源代码和测试用例。生成的软件在功能性和完整性方面优于现有的基于对话的多智能体系统。

- **设计阶段评估：** 实验表明，使用自然语言进行系统设计具有明显优势，智能体能够通过对话产生清晰、一致的设计方案，为后续编码阶段提供高质量的输入。

- **调试效率验证：** 研究发现，当智能体使用编程语言（而非自然语言）进行调试交流时，调试效率显著提高。这表明不同阶段应选择最合适的通信语言。

- **去幻觉效果：** 通信去幻觉机制有效降低了代码生成中的幻觉率，提高了生成代码的可运行性和正确性。

- **对比实验：** 与现有的单一 LLM 代码生成方法相比，ChatDev 的多智能体协作方式在软件质量、设计合理性和代码可维护性方面均有提升。

- **语言统一性验证：** 实验证实了语言通信作为 LLM 智能体间协作桥梁的有效性，展示了自然语言和编程语言在不同场景下的互补优势。

## 相关论文

<!-- 待填充：添加相关论文链接 -->

## 相关概念

- [智能体](../../concepts/ai-agents.html)
- [大语言模型](../../concepts/large-language-model.html)


## 分析信息

- **分析来源:** pdf_analysis
- **分析置信度:** high
- **分析时间:** 2026-05-02 06:02
- **关键词:** LLM, large language model, RL, generation, 3D
- **PDF 路径:** /root/wiki/raw/papers/2307-07924.pdf

---
*导入时间: 2026-05-01 23:30*
*导入方式: url*
