---
layout: paper
title: "KV-Fold: One-Step KV-Cache Recurrence for Long-Context Inference"
created: 2026-05-13
updated: 2026-05-13
type: paper
arxiv_id: 2605.12471v1
authors: "Alireza Nadali, Patrick Cooper, Ashutosh Trivedi, Alvaro Velasquez"
published: 2026-05-12
categories: cs.LG, cs.AI, cs.CL
tags: [ml, ai, nlp, benchmark]
source_url: https://arxiv.org/abs/2605.12471v1
pdf_url: https://arxiv.org/pdf/2605.12471v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: []
---

# KV-Fold: One-Step KV-Cache Recurrence for Long-Context Inference

## 基本信息

- **arXiv ID:** [2605.12471v1](https://arxiv.org/abs/2605.12471v1)
- **作者:** Alireza Nadali, Patrick Cooper, Ashutosh Trivedi et al.
- **发布日期:** 2026-05-12
- **分类:** cs.LG, cs.AI, cs.CL
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2605.12471v1)


## 摘要

### English

We introduce KV-Fold, a simple, training-free long-context inference protocol that treats the key-value (KV) cache as the accumulator in a left fold over sequence chunks. At each step, the model processes the next chunk conditioned on the accumulated cache, appends the newly produced keys and values, and passes the enlarged cache forward; the same one-step update is applied repeatedly, analogous to foldl in functional programming. Building on the KV cache concatenation primitive introduced for latent multi-agent communication, we repurpose it as a chunk-to-chunk recurrence for long-context inference. When processing chunk t, the model attends to the KV cache carried from earlier chunks as a prefix, reusing its internal state across segments without modifying or retraining the model. Despite its simplicity, the induced recurrence is stable: per-step drift rises briefly and then saturates into a flat plateau that persists across deep chains. This plateau is insensitive to a 10,000x change in numerical precision, robust across chunk sizes, and consistent across model families. At the task level, KV-Fold preserves exact information over long distances. On a needle-in-a-haystack benchmark, it achieves 100% exact-match retrieval across 152 trials spanning contexts from 16K to 128K tokens and chain depths up to 511 on Llama-3.1-8B, while remaining within the memory limits of a single 40GB GPU. Compared to streaming methods, which trade fidelity for bounded memory, KV-Fold maintains long-range retrieval while operating as a sequence of tractable forward passes. Overall, our results show that frozen pretrained transformers already support a stable form of KV-cache recurrence, providing a practical route to long-context inference without architectural changes or training.

### 中文

我们引入了 KV-Fold，这是一种简单的、免训练的长上下文推理协议，它将键值 (KV) 缓存视为序列块左折叠中的累加器。在每一步中，模型都会根据累积的缓存处理下一个块，附加新生成的键和值，并将扩大的缓存向前传递；重复应用相同的一步更新，类似于函数式编程中的foldl。基于为潜在多代理通信引入的 KV 缓存串联原语，我们将其重新调整为用于长上下文推理的块到块递归。当处理块 t 时，模型会关注从早期块携带的 KV 缓存作为前缀，跨段重用其内部状态，而无需修改或重新训练模型。尽管它很简单，但诱导的重复是稳定的：每步漂移短暂上升，然后饱和到在深链中持续存在的平坦平台。该平台对数值精度 10,000 倍的变化不敏感，在块大小上具有鲁棒性，并且在模型系列中保持一致。在任务层面，KV-Fold 可以长距离保存准确的信息。在大海捞针基准测试中，它在 Llama-3.1-8B 上跨越 16K 到 128K 令牌的上下文以及高达 511 的链深度的 152 次试验中实现了 100% 精确匹配检索，同时保持在单个 40GB GPU 的内存限制内。与以保真度换取有限内存的流方法相比，KV-Fold 在作为一系列易于处理的前向传递进行操作的同时，保持了远程检索。总的来说，我们的结果表明，冻结的预训练 Transformer 已经支持稳定形式的 KV 缓存循环，为长上下文推理提供了一条实用的途径，而无需进行架构更改或训练。

## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [基准评估](../../concepts/benchmarking.html)
- [AI安全与对齐](../../concepts/ai-safety-alignment.html)
- [智能体](../../concepts/ai-agents.html)

## 核心贡献

### English

KV-Fold is a simple, training-free long-context inference protocol that turns a frozen pretrained transformer into a recurrent model by carrying the accumulated KV cache across chunks as a left-fold accumulator. It achieves 100% exact-match needle-in-a-haystack retrieval across 152 trials spanning 16K-128K token contexts and chain depths up to 511 on Llama-3.1-8B on a single 40GB GPU. The induced recurrence is stable: per-step drift saturates into a flat plateau that persists across deep chains, is insensitive to a 10,000× change in numerical precision, and consistent across model families.

### 中文

KV-Fold 是一种简单、无需训练的长上下文推理协议，通过将累积的 KV 缓存作为左折叠累加器跨块传递，将冻结的预训练 Transformer 变为循环模型。它在 Llama-3.1-8B 上，在单个 40GB GPU 上，跨越 16K-128K token 上下文和高达 511 的链深度的 152 次试验中，实现了 100% 精确匹配的大海捞针检索。引发的循环是稳定的：每步漂移饱和为在深链中持续存在的平坦平台，对数值精度 10,000 倍的变化不敏感，且在模型系列间保持一致。

## 方法概述

### English

The sequence is split into fixed-size chunks. When processing chunk t, the model attends to the accumulated KV cache from chunks 1..t-1 as an attention prefix, generates output for chunk t, and appends the new KV entries to the cache for chunk t+1. This is analogous to foldl in functional programming — the same one-step update is applied repeatedly. No architectural changes, special memory tokens, or fine-tuning are required. The model parameters stay frozen; only the inference-time KV cache management is modified. Working memory grows linearly with total sequence length but remains bounded well below full-attention requirements.

### 中文

序列被分割为固定大小的块。处理块 t 时，模型将来自块 1..t-1 的累积 KV 缓存作为注意力前缀，为块 t 生成输出，并将新的 KV 条目追加到缓存中供块 t+1 使用。这类似于函数式编程中的 foldl——重复应用相同的一步更新。无需架构更改、特殊记忆 token 或微调。模型参数保持冻结；仅修改推理时的 KV 缓存管理。工作内存随总序列长度线性增长，但仍远低于全注意力需求。

## 实验结果

### English

KV-Fold achieves 100% exact-match retrieval at all tested distances (16K-128K tokens, chain depths 1-511) on Llama-3.1-8B, while StreamingLLM falls to 0% once the needle exits its 1024-token window. Per-step drift rises briefly (first ~10 transitions) then saturates into a flat plateau, not accumulating with chain depth. This plateau is stable under bfloat16 vs. float32 (10,000× precision difference), consistent across Llama-3.1-8B, Qwen-2.5-7B, and Gemma-2-9B, and robust across chunk sizes from 64 to 1024 tokens. At T=128K, KV-Fold uses 35.6GB peak memory on an A100 40GB and completes in 171s.

### 中文

KV-Fold 在 Llama-3.1-8B 上，在所有测试距离（16K-128K token，链深度 1-511）上实现了 100% 精确匹配检索，而 StreamingLLM 一旦 needle 退出其 1024 token 窗口就降至 0%。每步漂移短暂上升（前约 10 次转换）后饱和为平坦平台，不随链深度累积。该平台在 bfloat16 vs. float32（10,000 倍精度差异）下稳定，在 Llama-3.1-8B、Qwen-2.5-7B 和 Gemma-2-9B 间一致，且在 64 到 1024 token 的块大小间鲁棒。在 T=128K 时，KV-Fold 在 A100 40GB 上使用 35.6GB 峰值内存，耗时 171 秒。

## 局限性与注意点

### English

KV cache grows linearly with total sequence length, increasing memory and per-step latency — not suitable for unbounded streaming. The protocol does not compress or summarize past context, so memory cost eventually exceeds hardware limits for very long sequences. All experiments use a fixed temperature of 0, which may mask stochastic drift effects. The needle-in-a-haystack benchmark is a single-fact retrieval task; more complex reasoning across long contexts is not tested. The method has not been evaluated on production-scale models (e.g., 70B+). The linear growth in compute means very deep chains become slow despite being feasible.

### 中文

KV 缓存随总序列长度线性增长，增加了内存和每步延迟——不适用于无界流式处理。该协议不压缩或总结过去的上下文，因此对于极长序列，内存成本最终会超出硬件限制。所有实验使用温度 0，可能掩盖了随机漂移效应。大海捞针基准是单一事实检索任务；未测试跨长上下文的更复杂推理。该方法未在生产规模模型（如 70B+）上评估。计算的线性增长意味着尽管可行，非常深的链仍会变得缓慢。

---
*导入时间: 2026-05-13 06:02*
*来源: arXiv Daily Wiki Update 2026-05-13*
