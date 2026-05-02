---
layout: paper
title: "Crab: A Semantics-Aware Checkpoint/Restore Runtime for Agent Sandboxes"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28138v1
authors: "Tianyuan Wu, Chaokun Chang, Lunxi Cao, Wei Gao, Wei Wang"
published: 2026-04-30
categories: cs.OS, cs.AI
tags: [ai]
source_url: https://arxiv.org/abs/2604.28138v1
pdf_url: https://arxiv.org/pdf/2604.28138v1
source_type: arxiv_daily
confidence: medium
status: needs_pdf_lm_analysis
key_figures: [assets/papers/2604-28138v1/fig1.png, assets/papers/2604-28138v1/fig2.png, assets/papers/2604-28138v1/fig3.png]
---

# Crab: A Semantics-Aware Checkpoint/Restore Runtime for Agent Sandboxes

## 基本信息

- **arXiv ID:** [2604.28138v1](https://arxiv.org/abs/2604.28138v1)
- **作者:** Tianyuan Wu, Chaokun Chang, Lunxi Cao et al.
- **发布日期:** 2026-04-30
- **分类:** cs.OS, cs.AI
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2604.28138v1)

## 摘要

Autonomous agents act through sandboxed containers and microVMs whose state spans filesystems, processes, and runtime artifacts. Checkpoint and restore (C/R) of this state is needed for fault tolerance, spot execution, RL rollout branching, and safe rollback-yet existing approaches fall into two extremes: application-level recovery preserves chat history but misses OS-side effects, while full per-turn checkpointing is correct but too expensive under dense co-location. The root cause is an agent-OS semantic gap: agent frameworks see tool calls but not their OS effects; the OS sees state changes but lacks turn-level context to judge recovery relevance. This gap hides massive sparsity: over 75% of agent turns produce no recovery-relevant state, so most checkpoints are unnecessary. Crab (Checkpoint-and-Restore for Agent SandBoxes) is a transparent host-side runtime that bridges this gap without modifying agents or C/R backends. An eBPF-based inspector classifies each turn's OS-visible effects to decide checkpoint granularity; a coordinator aligns checkpoints with turn boundaries and overlaps C/R with LLM wait time; and a host-scoped engine schedules checkpoint traffic across co-located sandboxes. On shell-intensive and code-repair workloads, Crab raises recovery correctness from 8% (chat-only) to 100%, cuts checkpoint traffic by up to 87%, and stays within 1.9% of fault-free execution time.

## 深度解读状态

> 待 PDF 下载并由 LM 阅读后补充。本文详情页不会使用 arXiv 元数据或摘要快速导读冒充完整解读。

## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [强化学习](../../concepts/reinforcement-learning.html)
- [自动驾驶](../../concepts/autonomous-driving.html)
- [智能体](../../concepts/ai-agents.html)

---
*导入时间: 2026-05-02 16:44*
*来源: arXiv Daily Wiki Update 2026-05-02*
