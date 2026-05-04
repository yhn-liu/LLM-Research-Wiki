---
layout: paper
title: "When RAG Chatbots Expose Their Backend: An Anonymized Case Study of Privacy and Security Risks in Patient-Facing Medical AI"
created: 2026-05-04
updated: 2026-05-04
type: paper
arxiv_id: 2605.00796v1
authors: "Alfredo Madrid-García, Miguel Rujas"
published: 2026-05-01
categories: cs.CR, cs.AI, cs.CL
tags: [ai, nlp]
source_url: https://arxiv.org/abs/2605.00796v1
pdf_url: https://arxiv.org/pdf/2605.00796v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: [assets/papers/2605-00796v1/fig1.png]
---

# When RAG Chatbots Expose Their Backend: An Anonymized Case Study of Privacy and Security Risks in Patient-Facing Medical AI

## 基本信息

- **arXiv ID:** [2605.00796v1](https://arxiv.org/abs/2605.00796v1)
- **作者:** Alfredo Madrid-García (独立研究员), Miguel Rujas (Universidad Politécnica de Madrid)
- **发布日期:** 2026-05-01
- **分类:** cs.CR, cs.AI, cs.CL
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2605.00796v1)

## 关键图示

<div class="paper-figure-grid">
<figure><img src="../../assets/papers/2605-00796v1/fig1.png" alt="Figure 1: Two-stage workflow of the security assessment"><figcaption>Figure 1: 安全评估的两阶段工作流程。第一阶段由 Claude Opus 4.6 辅助的探索性测试和假设生成，第二阶段使用 Chrome 开发者工具进行手动验证。</figcaption></figure>
</div>

## 摘要

Background: Patient-facing medical chatbots based on retrieval-augmented generation (RAG) are increasingly promoted to deliver accessible, grounded health information. AI-assisted development lowers the barrier to building them, but they still demand rigorous security, privacy, and governance controls. Objective: To report an anonymized, non-destructive security assessment of a publicly accessible patient-facing medical RAG chatbot and identify governance lessons for safe deployment. Methods: A two-stage strategy. First, Claude Opus 4.6 supported exploratory prompt-based testing and structured vulnerability hypotheses. Second, candidate findings were manually verified using Chrome Developer Tools. Results: The LLM-assisted phase identified a critical vulnerability: sensitive system and RAG configuration appeared exposed through client-server communication. Manual verification confirmed that ordinary browser inspection allowed collection of the system prompt, model and embedding configuration, retrieval parameters, backend endpoints, API schema, document and chunk metadata, knowledge-base content, and the 1,000 most recent patient-chatbot conversations. The deployment also contradicted its privacy assurances: full conversation records were retrievable without authentication. Conclusions: Serious privacy and security failures in patient-facing RAG chatbots can be identified with standard browser tools, without specialist skills or authentication; independent review should be a prerequisite for deployment.

## 核心贡献

- 首次系统性地报告了面向患者的医疗 RAG 聊天机器人的真实安全评估案例，揭示了通过普通浏览器工具即可暴露的严重隐私和安全漏洞。
- 展示了商用 LLM（Claude Opus 4.6）在安全评估中的双重用途：在虚假"开发者"身份下，模型的安全控制未触发拒绝或限制，持续提供了安全测试支持。
- 发现的关键漏洞包括：完整 RAG 管线配置通过浏览器可见网络流量暴露、8 个知识库文档可完整枚举和重建、最近的 1,000 条患者对话记录可无认证访问。
- 提出了面向患者 RAG 系统的最低安全期望框架，涵盖配置管理、访问控制、数据管理、知识库治理、响应最小化、监控和独立审计等 8 个领域。

## 方法概述

研究者采用两阶段非破坏性评估策略。第一阶段利用 Claude Opus 4.6 进行 LLM 辅助探索：以虚假的"开发者安全测试"身份向 LLM 提出请求，LLM 协助设计了包括直接询问、角色覆盖、翻译、间接探测、JSON 格式、社会工程和创意写作等 8 类提示注入探针。LLM 还通过 Model Context Protocol 直接与部署的聊天机器人交互，系统性地收集 RAG 架构信息、源代码信息、知识库材料和历史对话。

第二阶段对所有候选发现进行手动验证。使用 Chrome 开发者工具从普通网站访问者视角检查三类浏览器可见流量：输入框自动触发的请求（状态检查和自动补全端点）、提交查询时的主请求（暴露了系统提示词、模型标识符、检索参数、向量数据库配置等）、以及响应生成期间的持久化请求。通过浏览器 JavaScript 控制台直接访问文档清单端点、文本块检索端点和对话存储端点，确认所有信息可在无认证条件下获取。

## 实验结果

- **RAG 管线配置暴露**：每个用户查询触发一个浏览器可见请求，暴露了操作提示词、活跃和备选 LLM 后端（7 个）、嵌入模型和 API 基础 URL、检索策略（相似度阈值、文本块窗口）、分块参数、摄入读取器等完整配置。
- **知识库完全可提取**：8 个精选文档（患者教育材料和科学文章）可通过无认证管理界面完全枚举。对每个文档披露了文件名、内部 UUID、每个文本块的内容、检索相似度评分和嵌入器标识符。
- **患者对话记录暴露**：一个公开接口返回最近 1,000 条患者-聊天机器人对话记录，包含用户提交的问题、模型响应、时间戳和关键词分类，记录跨越多个月份，涵盖多语言查询。
- **公开声明与部署实际不符**：公布的隐私描述声称"不存储个人信息或聊天历史"，但部署实际以无认证方式持久化和暴露了完整对话记录。系统提示词也与公布的"专业构建、版本控制、以患者为中心"描述不符。
- **所有用于指导 LLM 辅助评估的提示均未被 Claude Opus 4.6 的安全控制拒绝、阻止或限制**。

## 局限性与注意点

- 研究结果仅描述了一个匿名化部署，不应推广到所有 RAG 系统。但该模式可能具有更广泛的关联性：原型框架和演示默认配置在转入生产环境时可能成为临床风险。
- 论文中刻意省略或泛化了可能支持复现或滥用的技术细节。
- 研究未涉及识别或去匿名化用户 IP 地址、访问服务器日志等操作。

## 相关概念

- [大语言模型](../../concepts/large-language-model.html)
- [医学AI](../../concepts/medical-ai.html)

---
*导入时间: 2026-05-04 06:01*
*来源: arXiv Daily Wiki Update 2026-05-04*
