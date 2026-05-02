---
layout: paper
title: "Claw-Eval-Live: A Live Agent Benchmark for Evolving Real-World Workflows"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28139v1
authors: "Chenxin Li, Zhengyang Tang, Huangxin Lin, Yunlong Lin, Shijue Huang, Shengyuan Liu, Bowen Ye, Rang Li"
published: 2026-04-30
categories: cs.SE, cs.AI
tags: [ai, benchmark]
source_url: https://arxiv.org/abs/2604.28139v1
pdf_url: https://arxiv.org/pdf/2604.28139v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: [assets/papers/2604-28139v1/fig1.png, assets/papers/2604-28139v1/fig2.png, assets/papers/2604-28139v1/fig3.png]
---

# Claw-Eval-Live: A Live Agent Benchmark for Evolving Real-World Workflows

## 基本信息

- **arXiv ID:** [2604.28139v1](https://arxiv.org/abs/2604.28139v1)
- **作者:** Chenxin Li, Zhengyang Tang, Huangxin Lin et al.
- **发布日期:** 2026-04-30
- **分类:** cs.SE, cs.AI
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2604.28139v1)

## 关键图示

<div class="paper-figure-grid">
<figure><img src="../../assets/papers/2604-28139v1/fig1.png" alt="Claw-Eval-Live Figure 1"><figcaption>Figure 1</figcaption></figure>
<figure><img src="../../assets/papers/2604-28139v1/fig2.png" alt="Claw-Eval-Live Figure 2"><figcaption>Figure 2</figcaption></figure>
<figure><img src="../../assets/papers/2604-28139v1/fig3.png" alt="Claw-Eval-Live Figure 3"><figcaption>Figure 3</figcaption></figure>
</div>

## 摘要

LLM agents are expected to complete end-to-end units of work across software tools, business services, and local workspaces. Yet many agent benchmarks freeze a curated task set at release time and grade mainly the final response, making it difficult to evaluate agents against evolving workflow demand or verify whether a task was executed. We introduce Claw-Eval-Live, a live benchmark for workflow agents that separates a refreshable signal layer, updated across releases from public workflow-demand signals, from a reproducible, time-stamped release snapshot. Each release is constructed from public workflow-demand signals, with ClawHub Top-500 skills used in the current release, and materialized as controlled tasks with fixed fixtures, services, workspaces, and graders. For grading, Claw-Eval-Live records execution traces, audit logs, service state, and post-run workspace artifacts, using deterministic checks when evidence is sufficient and structured LLM judging only for semantic dimensions. The release contains 105 tasks spanning controlled business services and local workspace repair, and evaluates 13 frontier models under a shared public pass rule. Experiments reveal that reliable workflow automation remains far from solved: the leading model passes only 66.7% of tasks and no model reaches 70%. Failures are structured by task family and execution surface, with HR, management, and multi-system business workflows as persistent bottlenecks and local workspace repair comparatively easier but unsaturated. Leaderboard rank alone is insufficient because models with similar pass rates can diverge in overall completion, and task-level discrimination concentrates in a middle band of tasks. Claw-Eval-Live suggests that workflow-agent evaluation should be grounded twice, in fresh external demand and in verifiable agent action.

## 核心贡献

- **提出“live snapshot”式工作流智能体基准。** Claw-Eval-Live 试图同时解决两个矛盾：基准需要固定快照保证可复现，又需要跟随真实自动化需求变化。论文把可刷新的公共信号层与固定发布层分离：未来 release 可重新采集信号，但已发布任务、fixtures、graders 保持不变。
- **从公共需求信号构造任务分布。** 当前版本以 ClawHub Top-500 popular skills 为上游代理信号，经 pattern clustering、family weighting、seed expansion、candidate implementation/pilot screening，再用 MILP 从 157 个可运行候选中选出 105 个公开任务。
- **把评测对象定义为完整执行轨迹。** 每个任务不是单纯 prompt，而包含 task.yaml、工具 schema、服务 fixture、工作区文件和 task-specific grader；评分依据工具调用、服务审计日志、状态变更、命令痕迹、生成 artifact，而不是最终回答文本。
- **提出 action-grounded hybrid grading。** 评分先用确定性证据检查数据检索、数据准确性、动作执行；只有语义组织、报告完整性等无法精确匹配的维度才使用带 rubric 的结构化 LLM judging，且 judge 输入必须基于已收集 trace。
- **给出 13 个前沿模型的公开快照结果。** 论文展示当前 agents 距可靠工作流自动化仍有明显距离，并指出难点集中在跨服务商业流程、HR、management、multi-system coordination，而不是简单终端修复。

## 方法概述

- **信号到任务的五阶段管线：** 先采集带时间戳的 ClawHub Top-500 信号；再按用户目标、操作对象、执行面聚类成 workflow pattern；将 pattern 质量转成 family 权重；扩展为任务 seed 并实现为可执行候选；最后用覆盖、规模、判别力约束选择公开子集。
- **MILP 公开子集选择：** 变量表示候选任务是否入选，约束包括目标任务数、每个细粒度 family 至少覆盖一个任务、剔除 pilot 阶段零判别任务；目标倾向保留能维持 top-K pilot 模型相对排序的任务。这使任务选择比纯人工挑选更可审计。
- **执行环境：** 当前 105 个任务包含 87 个 service-backed workflows 和 18 个 terminal/workspace repair。前者涉及 CRM、finance、email、calendar、helpdesk、knowledge base 等受控服务；后者要求检查文件/日志、运行命令、修改 artifact 并通过验证脚本。
- **评分证据：** 常见权重包括 Data Retrieval 约 15–20%、Data Accuracy 约 40–60%、Action Verification 约 10–20%；workspace repair 的 SHELL/W-family 任务可完全确定性评分，分析/撰写类任务才叠加 GPT-5.4 judge 的语义维度。
- **公开指标：** 主要报告 Pass Rate 与 Overall Completion Score。任务得分 `s_{t,m}` 在 `[0,1]`，公开 pass 阈值 `τ=0.80`；排名先按 Pass Rate，再按 Overall。

## 实验结果

- **总体排行榜：** 13 个模型中 Claude Opus 4.6 以 66.7% pass rate、83.6 overall 第一；GPT-5.4 为 63.8%、81.7；Claude Sonnet 4.6 和 GLM-5 都是 61.9% pass rate，但 overall 不同。没有模型超过 70% pass rate。
- **族级差异显著：** Development/Terminal 对强模型接近天花板，Claude Opus 4.6、GPT-5.4、Claude Sonnet 4.6 在该组达到 100%；HR/People 极难，没有模型超过 22.2%，若干模型为 0%。Productivity 展开最大，从 88.0% 到 48.0%。
- **执行面差异：** 本地 workspace/terminal 18 题对所有模型至少 72.2%，多个模型接近或达到 100%；但 87 个 service-backed workflows 中没有模型超过 59.8%。论文将主要瓶颈定位为跨系统证据收集、状态更新、记录链接和商业流程闭环。
- **阈值与判别力：** 在公开 0.80 pass 阈值下，105 题中有 19 个全模型通过、27 个全模型失败，判别力集中在中间地带；高判别任务包括 ecommerce monthly reconcile、first response time audit、multi-doc merge 等多源精确抽取任务。
- **效率对比：** GPT-5.4 在前四名中 tokens、时间、估算成本较优；Claude Opus 4.6 准确率最高但估算 API 成本更高。论文强调部署选择应看 family-level accuracy 与成本约束，而非只看总榜。

## 局限性与注意点

- **公共信号不是现实需求真值。** ClawHub Top-500 只是可检查的上游代理，不能直接代表企业部署频率、经济价值或任务难度；release 的“live”性取决于该信号源是否真正反映用户需求。
- **LLM judge 仍可能引入偏差。** 论文承认 GPT-5.4 同时是 judge 和被评模型之一；虽然 judge 只用于语义维度并被 trace/rubric 约束，但仍不能等同于独立人类裁决。
- **当前快照覆盖仍有限。** 105 个任务、18 个服务和 sandbox workspace 可复现，但不可能覆盖所有真实企业工具、权限模型、长周期流程、多人协作或安全约束。
- **阈值会影响结论。** 公开 pass threshold 为 0.80，使一部分任务变成 all-pass/all-fail；应结合 Overall Completion、任务族、执行面和 task-level discrimination 解读，而非把 pass rate 当唯一能力度量。
- **“live”刷新可能带来跨 release 可比性问题。** 已发布快照内部可复现，但如果未来任务分布随信号变化，跨季度模型趋势需要区分模型进步与任务分布改变。

## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [智能体](../../concepts/ai-agents.html)
- [基准评估](../../concepts/benchmarking.html)
- [工具使用](../../concepts/tool-use.html)

---
*导入时间: 2026-05-02 16:44*
*来源: arXiv Daily Wiki Update 2026-05-02*
