# 科研知识库 Schema

## Domain
AI/ML/NLP/CV 领域的科研知识库，专注于：
- 自然语言处理（NLP）
- 计算机视觉（CV）
- 机器学习（ML）
- 人工智能（AI）
- 公共健康 + AI 交叉领域

## Conventions
- 文件名：小写，连字符，无空格（如 `transformer-architecture.md`）
- 每个 wiki 页面必须有 YAML frontmatter
- 使用 `[[wikilinks]]` 链接其他页面（每个页面至少 2 个出站链接）
- 更新页面时，必须更新 `updated` 日期
- 每个新页面必须添加到 `index.md`
- 每个操作必须记录到 `log.md`

## Frontmatter 标准

### 论文页面
```yaml
---
title: 论文标题
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: paper
arxiv_id: 2604.xxxxx
authors: [Author1, Author2, ...]
published: YYYY-MM-DD
categories: [cs.CL, cs.CV, ...]
tags: [from taxonomy]
source_url: https://arxiv.org/abs/xxxx
pdf_url: https://arxiv.org/pdf/xxxx
confidence: high | medium | low
status: unread | reading | read | summarized
---
```

### 模型/方法页面
```yaml
---
title: 模型/方法名称
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: model | method
tags: [from taxonomy]
related_papers: [paper-slug1, paper-slug2]
confidence: high | medium | low
---
```

### 概念页面
```yaml
---
title: 概念名称
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: concept
tags: [from taxonomy]
related_papers: [paper-slug1, paper-slug2]
---
```

## Tag 分类体系

### 研究领域
- `nlp` - 自然语言处理
- `cv` - 计算机视觉
- `ml` - 机器学习
- `ai` - 人工智能
- `health-ai` - 公共健康 + AI
- `multimodal` - 多模态
- `reinforcement-learning` - 强化学习

### 模型架构
- `transformer` - Transformer 架构
- `diffusion` - 扩散模型
- `gan` - 生成对抗网络
- `gnn` - 图神经网络
- `cnn` - 卷积神经网络
- `rnn` - 循环神经网络
- `mamba` - 状态空间模型

### 任务类型
- `classification` - 分类
- `generation` - 生成
- `extraction` - 抽取
- `summarization` - 摘要
- `translation` - 翻译
- `qa` - 问答
- `detection` - 检测
- `segmentation` - 分割

### 训练技术
- `pretraining` - 预训练
- `finetuning` - 微调
- `rlhf` - RLHF
- `dpo` - DPO
- `lora` - LoRA
- `quantization` - 量化
- `distillation` - 蒸馏

### 数据相关
- `dataset` - 数据集
- `benchmark` - 基准测试
- `annotation` - 标注
- `synthetic-data` - 合成数据

### 应用领域
- `medical` - 医疗
- `robotics` - 机器人
- `autonomous` - 自动驾驶
- `recommendation` - 推荐系统
- `search` - 搜索

### 元标签
- `survey` - 综述
- `state-of-the-art` - SOTA
- `open-source` - 开源
- `controversial` - 有争议
- `important` - 重要

## 页面创建规则

### 论文页面
- **创建条件**：arXiv 每日推荐的论文自动创建
- **内容要求**：
  - 标题、作者、摘要（中英双语）
  - 核心贡献
  - 方法概述
  - 实验结果
  - 相关论文链接

### 模型/方法页面
- **创建条件**：出现在 2+ 篇论文中，或是一篇论文的核心
- **内容要求**：
  - 定义和描述
  - 架构图（如果有）
  - 关键特性
  - 相关论文

### 概念页面
- **创建条件**：出现在 2+ 篇论文中
- **内容要求**：
  - 定义
  - 当前研究状态
  - 开放问题
  - 相关概念和论文

## Update Policy

当新论文与现有内容冲突时：
1. 检查日期——新论文通常优于旧论文
2. 如果真的矛盾，同时记录两个观点，标注日期和来源
3. 在 frontmatter 中标记：`contested: true`
4. 在 lint 报告中标记供用户审阅

## 定期维护

### 每日自动
- arXiv 每日推荐自动导入
- 更新 index.md
- 记录 log.md

### 每周手动（可选）
- Lint 检查：孤立页面、缺失链接、过期内容
- 更新重要论文的 status
- 整理概念和模型页面

## Wiki 路径
**位置：** `~/wiki`（默认）
**环境变量：** `WIKI_PATH`（可自定义）
