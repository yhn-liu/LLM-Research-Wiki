# 科研知识库 Schema

## Domain
AI/ML/NLP/CV 领域的科研知识库，专注于：
- 自然语言处理（NLP）
- 计算机视觉（CV）
- 机器学习（ML）
- 人工智能（AI）
- 公共健康 + AI 交叉领域

## 架构：维基式知识组织

本知识库采用**概念驱动、论文为据**的组织方式：

```
wiki/
├── index.md              # 首页：概念导航 + 论文索引
├── concepts/             # 概念页面（核心骨架）
│   ├── large-language-model.md
│   ├── reinforcement-learning.md
│   ├── multimodal-learning.md
│   └── ...
├── entities/
│   ├── papers/           # 论文页面
│   ├── models/           # 模型/方法页面
│   └── people/           # 人物/组织
├── comparisons/          # 对比分析
├── raw/                  # 原始论文 PDF（不可修改）
└── SCHEMA.md             # 本文件
```

### 三层结构
- **Layer 1 — Raw Sources:** `raw/` 目录，不可修改的原始论文
- **Layer 2 — Wiki Pages:** `concepts/`, `entities/`, `comparisons/`，Agent 创建和维护
- **Layer 3 — Schema:** 本文件，定义结构和规范

## Conventions
- 文件名：小写，连字符，无空格（如 `reinforcement-learning.md`）
- 每个 wiki 页面必须有 YAML frontmatter
- 使用 Markdown 链接 `[显示文本](路径)` 链接其他页面（每个页面至少 2 个出站链接）
- 更新页面时，必须更新 `updated` 日期
- 每个新页面必须添加到 `index.md`
- 每个操作必须记录到 `log.md`
- 所有内容使用**中文**

## 概念页面规范（concepts/）

### Frontmatter
```yaml
---
title: 概念名称
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: concept
tags: [relevant, tags]
papers: [paper-slug1, paper-slug2]
---
```

### 页面结构（文献中心式，非百科全书式）
1. **定义** — 2-3 句话的简洁定义
2. **关键文献与发现**（核心）— 按子主题组织本库论文，每篇提供一句话摘要 + 方法要点 + 关键发现
3. **研究趋势** — 跨论文综合分析，揭示联系和方向
4. **相关论文** — 完整论文索引（带链接）
5. **相关概念** — 链接到其他概念页面
6. 保留一段历史背景即可，不要大段发展时间线

### 页面创建规则
- 出现在 2+ 篇论文中的概念必须创建页面
- 核心研究方向（如自动驾驶、医学 AI）即使只有 1 篇论文也可创建
- 每个概念页面至少链接 2 篇论文或 2 个其他概念页面

## 论文页面规范（entities/papers/）

### Frontmatter
```yaml
---
title: "论文标题"
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: paper
arxiv_id: 2604.xxxxx
authors: "Author1, Author2, ..."
published: YYYY-MM-DD
categories: [cs.CL, cs.CV, ...]
tags: [from taxonomy]
source_url: https://arxiv.org/abs/xxxx
pdf_url: https://arxiv.org/pdf/xxxx
confidence: high | medium | low
status: unread | reading | read | analyzed
---
```

### 页面结构
1. **基本信息** — arXiv ID、作者、日期、分类
2. **摘要** — 完整的中英双语摘要（不可截断）
3. **核心贡献** — 3-5 点具体贡献
4. **方法概述** — 2-3 段技术描述
5. **实验结果** — 关键发现和数据
6. **相关概念** — 链接到概念页面

## 模型/方法页面规范（entities/models/）
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
- `gnn` - 图神经网络
- `mamba` - 状态空间模型

### 训练技术
- `pretraining` - 预训练
- `finetuning` - 微调
- `rlhf` - RLHF
- `dpo` - DPO
- `lora` - LoRA
- `quantization` - 量化
- `distillation` - 蒸馏

### 任务类型
- `classification` - 分类
- `generation` - 生成
- `extraction` - 抽取
- `summarization` - 摘要
- `qa` - 问答
- `detection` - 检测
- `reasoning` - 推理

### 应用领域
- `medical` - 医疗
- `autonomous` - 自动驾驶
- `education` - 教育

### 元标签
- `survey` - 综述
- `state-of-the-art` - SOTA
- `open-source` - 开源
- `important` - 重要

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
