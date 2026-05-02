---
layout: paper
title: "Leave No Context Behind: Efficient Infinite Context Transformers with Infini-attention"
created: 2026-05-01
updated: 2026-05-01
type: paper
arxiv_id: 2404.07143
authors: "Tsendsuren Munkhdalai, Manaal Faruqui, Siddharth Gopal"
published: 2024-04-10
categories: cs.CL, cs.AI, cs.LG
tags: [nlp, ml, ai, transformer, attention, long-context]
source_url: https://arxiv.org/abs/2404.07143
pdf_url: https://arxiv.org/pdf/2404.07143
source_type: url
confidence: high
status: analyzed
---

# Leave No Context Behind: Efficient Infinite Context Transformers with Infini-attention

## 基本信息

- **arXiv ID:** [2404.07143](https://arxiv.org/abs/2404.07143)
- **作者:** Tsendsuren Munkhdalai, Manaal Faruqui, Siddharth Gopal
- **发布日期:** 2024-04-10
- **分类:** cs.CL, cs.AI, cs.LG
- **导入类型:** url

## 摘要

### English

This work introduces an efficient method to scale Transformer-based Large Language Models (LLMs) to infinitely long inputs with bounded memory and computation. A key component in our proposed approach is a new attention technique dubbed Infini-attention. The Infini-attention incorporates a compressive memory into the vanilla attention mechanism and builds in both masked local attention and long-term linear attention mechanisms in a single Transformer block. We demonstrate the effectiveness of our approach on long-context language modeling benchmarks, 1M sequence length passkey context block retrieval and 500K length book summarization tasks with 1B and 8B LLMs. Our approach introduces minimal bounded memory parameters and enables fast streaming inference for LLMs.

### 中文

本工作提出了一种高效的方法，使基于Transformer的大语言模型（LLMs）能够处理无限长度的输入，同时保持有界的内存和计算开销。我们提出的方法中的关键组件是一种名为Infini-attention的新注意力技术。Infini-attention将压缩记忆整合到标准注意力机制中，并在单个Transformer块中同时构建了掩码局部注意力和长期线性注意力机制。我们在长上下文语言建模基准测试、100万序列长度的passkey上下文块检索任务以及50万长度的书籍摘要任务上验证了该方法的有效性，使用了1B和8B参数的LLMs。我们的方法引入了最小的有界记忆参数，并实现了LLMs的快速流式推理。

## 核心贡献

1. **提出Infini-attention机制**：将压缩记忆（compressive memory）整合到标准注意力机制中，在单个Transformer块内同时实现掩码局部注意力和长期线性注意力，从而在有界内存下处理无限长上下文。
2. **有界内存与计算的无限上下文扩展**：提出一种在固定内存和计算开销下将Transformer扩展到任意长度输入的方法，突破了标准注意力机制的二次复杂度限制。
3. **最小有界记忆参数设计**：引入仅需最小附加参数的有界记忆机制，使模型在处理超长序列时保持高效。
4. **支持快速流式推理**：方法天然支持流式推理，使得LLMs能够高效处理连续输入流。
5. **大规模实验验证**：在1B和8B参数的LLM上验证了方法在长上下文建模、passkey检索和书籍摘要等任务上的有效性。

## 方法概述

Infini-attention的核心思想是在标准注意力机制的基础上引入压缩记忆（compressive memory）来存储长期上下文信息。传统的Transformer注意力机制由于需要计算所有token对之间的注意力分数，其内存和计算复杂度随序列长度呈二次增长，这限制了模型处理超长输入的能力。Infini-attention通过维护一个固定大小的压缩记忆来捕获历史上下文信息，从而将内存需求控制在有界范围内。

在具体实现上，Infini-attention在单个Transformer块中同时集成了两种注意力机制：掩码局部注意力（masked local attention）用于处理当前窗口内的局部上下文，以及长期线性注意力（long-term linear attention）用于访问压缩记忆中的全局历史信息。这两种机制通过门控机制进行融合，使模型能够根据当前输入动态平衡局部信息和全局历史信息的利用。压缩记忆通过线性注意力更新，每一步的更新仅需固定大小的内存操作。

该设计使得Infini-attention可以无缝替换标准Transformer中的注意力层，无需改变模型的整体架构。通过将压缩记忆与局部注意力相结合，模型在保持高效计算的同时，能够有效处理远超标准注意力机制能力范围的超长序列输入。

## 实验结果

- **长上下文语言建模**：在1B和8B参数的LLM上展示了方法的有效性，能够在有限内存下处理任意长度的输入。
- **Passkey上下文块检索**：成功在100万（1M）序列长度的passkey检索任务中检索出隐藏的密钥信息，证明了模型对超长上下文的检索能力。
- **书籍摘要**：在50万（500K）长度的书籍摘要任务上取得有效结果，验证了方法在实际长文档理解任务中的实用性。
- **效率优势**：方法仅引入最小的有界记忆参数，同时支持快速流式推理，在内存效率和推理速度上均优于标准注意力机制。

## 分析信息

- **分析来源:** pdf_analysis
- **分析置信度:** high
- **分析时间:** 2026-05-01 21:13
- **关键词:** transformer, attention, LLM, long-context, compressive memory, Infini-attention
- **PDF 路径:** /root/wiki/raw/papers/2404-07143.pdf

---

*导入时间: 2026-05-01 19:55*
*导入方式: url*

## 相关概念

- [Transformer](../../concepts/transformer.html)
- [注意力机制](../../concepts/attention-mechanism.html)
- [大语言模型](../../concepts/large-language-model.html)
- [长上下文学习](../../concepts/long-context-learning.html)
- [压缩记忆](../../concepts/compressive-memory.html)
- [流式推理](../../concepts/streaming-inference.html)
