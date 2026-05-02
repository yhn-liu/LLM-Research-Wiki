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
confidence: high
status: analyzed
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

## 核心贡献

- **指出并量化 agent–OS 语义鸿沟。** 论文的核心观察不是“需要 checkpoint”本身，而是智能体框架只知道对话与工具调用，OS 只看见文件、进程和内存变化，二者都无法判断某一轮交互是否产生恢复相关状态。作者用 Terminal-Bench/SWE-Bench 轨迹说明，聊天级恢复在 Terminal-Bench 上只能达到 8–13% 正确率，chat+filesystem 也只有 28–42%，而逐轮全量 C/R 虽正确但在高密度共置时最高带来 3.78× 慢down。
- **提出 Crab：透明的宿主侧语义感知 C/R 运行时。** Crab 不修改 agent、LLM 或底层 C/R 后端，而是在 agent–LLM 控制路径和宿主 OS 观测路径之间建立联系：Coordinator 识别 turn boundary 并缓存请求/响应，eBPF Inspector 识别本轮是否改变文件系统或进程状态，C/R Engine 用 ZFS/CRIU/runc 等通用后端生成可恢复版本。
- **把 checkpoint 从“每轮必做”变为“按恢复相关状态自适应”。** Inspector 将每轮分为跳过、仅文件系统、仅进程或全量 checkpoint；Manager 用类似 git 版本历史的 manifest 组合最新文件系统与进程 artifact，并以事务式发布避免半成品恢复点。
- **面向真实部署处理两类 agent-sandbox 形态。** 对 agent-with-a-sandbox，Coordinator 会在恢复后重发 crash 前未完成的 sandbox 命令；对 agent-in-a-sandbox，Crab 排除 agent 进程本身以避免每轮进程 checkpoint，并用 fast-forward 机制用缓存响应跳过已完成 turn，避免重放动作破坏状态。
- **证明 C/R 可成为智能体能力，而不只是容错机制。** 论文还讨论 rollback 工具、spot/preemptible execution、speculative execution 和 TreeRL/RL rollout branching 等场景，说明低成本 fork/restore 能降低重跑、token 和回滚成本。

## 方法概述

Crab 的设计围绕“在 turn 边界恢复，而不是在任意 syscall 处恢复”。Coordinator 作为轻量代理位于 agent 与 LLM/工具交互路径上，记录每个 interaction turn，确定何时可以安全发布恢复点，并尽量把 checkpoint 执行重叠到等待 LLM 响应的窗口中。这样做的关键是假设 agent 工作流天然由“本地工具执行 → 等待模型输出”交替组成，C/R 的很多耗时可被 LLM latency 隐藏。

Inspector 运行在宿主侧，通过 eBPF 观测 sandbox 内 OS 可见副作用，包括文件写入/删除、进程创建退出、进程内存与长生命周期进程状态等。它不理解任务语义，但通过 turn 边界把这些低层事件聚合成“本轮净变化”，从而判断下一恢复点需要哪些 artifact。设计上宁可出现文件系统 false positive，也避免 false negative，因为多做一次文件 checkpoint 只增加少量成本，漏掉状态则会破坏恢复正确性。

C/R Engine 负责在多 sandbox 共置时调度 checkpoint I/O。Scheduler 按是否会阻塞前台执行来排序；Worker 调用 runc/CRIU/ZFS 等后端生成进程或文件系统 artifact；Manager 将部分 artifact 组合成版本化 manifest，例如新的文件系统状态可与最近一次进程状态配对。每个 checkpoint 经历 pending、dumping、versioning、done/failed 生命周期，只有完整 versioning 后才对恢复可见。

部署细节上，agent-in-a-sandbox 模式尤其棘手：如果把 agent 进程也纳入进程状态检测，几乎每轮都会产生内存变化，选择性 checkpoint 失效；但排除 agent 进程后，恢复时 agent 的逻辑进度可能落后于文件系统。Crab 用 Coordinator 缓存历史请求/响应，在 agent 重放旧请求时返回合成响应，直到其逻辑进度追上恢复点，避免重复执行已经体现在文件系统中的命令。

## 实验结果

实验覆盖 Terminal-Bench 与 SWE-Bench，包含 Claude-code、iFlow-cli、SWE-agent 三类配置，并在 AWS c6id.32xlarge 上评估 16 到 96 个 sandbox 共置密度。正确性方面，Crab、Restart 和逐轮 FullCkpt 都达到 100% 恢复正确率；Chat-only 在 Terminal-Bench 上仅 13%/8%，在 SWE-Bench 上 9%；Chat+FS 在 SWE-Bench 可达 100%，但在 Terminal-Bench 只有 28%/42%，说明终端任务常依赖长生命周期进程和运行时状态。

选择性 checkpoint 的稀疏性非常明显：Claude-code 的 Terminal-Bench 轨迹中 87% turn 可跳过、5% 仅需文件系统、8% 需全量；iFlow-cli 中 70% 可跳过、25% 文件系统、5% 全量；SWE-agent 中约 75% 可跳过、25% 文件系统，几乎不需要进程 checkpoint。作者还人工标注 2,063 个 iFlow-cli turn，Inspector 对进程变化 100% 准确，对文件系统变化 98.3% 准确，且两者 false negative 都为 0。

性能上，在每个任务注入一次 crash 的场景中，Crab 的端到端时间仍在无故障、无 checkpoint 最优执行的 0–1.9% 内；Restart 因重做已完成工作最高慢 1.67×；FullCkpt 在 Terminal-Bench 高密度下因进程 checkpoint 与存储争用最高慢 3.78×。组件开销也较小：Coordinator 每 turn 只有几十微秒；Inspector median 约 31–72 ms，p95 低于 200 ms；checkpoint dump 的 p50/p95/p99 为 0.1/0.7/1.0 s，长尾主要由进程 dump 造成。

## 局限性与注意点

- 论文主要在可回放的 benchmark 轨迹和特定 agent/LLM 组合上评估，真实生产系统中工具 API、长期后台服务、网络连接和外部副作用更复杂，是否都能被宿主侧观测与恢复需要进一步验证。
- Crab 的正确性依赖 turn boundary 的识别、Coordinator 记录完整性以及 eBPF 事件覆盖；若工具调用绕过记录路径或内核事件被过滤，选择性 checkpoint 可能漏掉关键状态。
- 文件系统 false positive 被认为成本低，但在更大镜像、更高写放大或远程存储环境下，保守策略可能放大 I/O 压力。
- 当前实现基于 Linux 容器/微VM、CRIU/ZFS/runc 等后端，跨 OS、GPU/加速器状态、外部数据库连接或分布式 sandbox 的适用性未被充分证明。


## 相关概念

- [智能体](../../concepts/ai-agents.html)
- [大语言模型](../../concepts/large-language-model.html)
- [强化学习](../../concepts/reinforcement-learning.html)
- [操作系统](../../concepts/operating-systems.html)
- [沙箱环境](../../concepts/sandbox-environments.html)


---
*导入时间: 2026-05-02 16:44*
*来源: arXiv Daily Wiki Update 2026-05-02*
