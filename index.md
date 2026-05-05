---
layout: default
title: LLM Research Wiki
---

# 🔬 LLM Research Wiki

> AI/ML 领域的维基式知识库。按概念组织，论文为据，持续更新。
> 最后更新：2026-05-05 | 概念：61 | 论文：52

---

## 🌟 今日新论文

> 2026-05-05 自动更新，共 10 篇。这里是网站版每日论文导读；点击标题进入论文页面查看摘要、方法信号、相关主题和关键图示。

<div class="daily-papers">
<div class="daily-paper-card">
  <a href="entities/papers/2605-02888v1-speckv-adaptive-speculative-decoding-with-compress.html" class="daily-thumb"><img src="assets/papers/2605-02888v1/fig1.png" alt="SpecKV: Adaptive Speculative Decoding with Compression-Aware Gamma Selection"></a>
  <div class="daily-paper-body">
    <h3><a href="entities/papers/2605-02888v1-speckv-adaptive-speculative-decoding-with-compress.html">SpecKV: Adaptive Speculative Decoding with Compression-Aware Gamma Selection</a></h3>
    <div class="daily-meta">2026-05-04 · cs.LG, cs.AI, cs.CL · 大语言模型</div>
    <p><strong>方法/亮点：</strong>In this paper, we present \textbf{SpecKV}, a lightweight adaptive controller that selects~$γ$ per speculation step using signals extracted from the draft model itself.</p>
    <p class="daily-abstract"><strong>摘要（中文）：</strong>推测性解码通过使用小型草稿模型提出供较大目标模型验证的候选标记来加速大型语言模型 (LLM) 推理。此过程中的一个关键超参数是推测长度~$γ$，它决定草稿模型每一步提出多少个令牌。 Nearly all existing systems use a fixed~$γ$ (typically~4), yet empirical evidence suggests that the optimal value varies across t...</p>
    <p class="daily-abstract"><strong>Abstract:</strong> Speculative decoding accelerates large language model (LLM) inference by using a small draft model to propose candidate tokens that a larger target model verifies. A critical hyperparameter in this process is the specula...</p>
  </div>
</div>
<div class="daily-paper-card">
  <a href="entities/papers/2605-02815v1-flexsql-flexible-exploration-and-execution-make-be.html" class="daily-thumb"><img src="assets/papers/2605-02815v1/fig1.png" alt="FlexSQL: Flexible Exploration and Execution Make Better Text-to-SQL Agents"></a>
  <div class="daily-paper-body">
    <h3><a href="entities/papers/2605-02815v1-flexsql-flexible-exploration-and-execution-make-be.html">FlexSQL: Flexible Exploration and Execution Make Better Text-to-SQL Agents</a></h3>
    <div class="daily-meta">2026-05-04 · cs.CL · 智能体</div>
    <p><strong>方法/亮点：</strong>We present FlexSQL, a text-to-SQL agent whose core design principle is flexible database interaction: the agent can explore schema structure, inspect data values, and run verification queries at any point during reasoning.</p>
    <p class="daily-abstract"><strong>摘要（中文）：</strong>Text-to-SQL over large analytical databases requires navigating complex schemas, resolving ambiguous queries, and grounding decisions in actual data. Most current systems follow a fixed pipeline where schema elements are...</p>
    <p class="daily-abstract"><strong>Abstract:</strong> Text-to-SQL over large analytical databases requires navigating complex schemas, resolving ambiguous queries, and grounding decisions in actual data. Most current systems follow a fixed pipeline where schema elements are...</p>
  </div>
</div>
<div class="daily-paper-card">
  
  <div class="daily-paper-body">
    <h3><a href="entities/papers/2605-02801v1-reinforcement-learning-for-llm-based-multi-agent-s.html">Reinforcement Learning for LLM-based Multi-Agent Systems through Orchestration Traces</a></h3>
    <div class="daily-meta">2026-05-04 · cs.CL · 大语言模型 / 强化学习 / 基准评估 / 图神经网络</div>
    <p><strong>方法/亮点：</strong>As large language model (LLM) agents evolve from isolated tool users into coordinated teams, reinforcement learning (RL) must optimize not only individual actions but also how work is spawned, delegated, communicated, aggregated, and stoppe</p>
    <p class="daily-abstract"><strong>摘要（中文）：</strong>随着大型语言模型 (LLM) 代理从孤立的工具用户发展为协调的团队，强化学习 (RL) 不仅必须优化个人操作，还必须优化工作的产生、委托、沟通、聚合和停止方式。本文通过编排跟踪研究基于 LLM 的多智能体系统的强化学习：时间交互图，其事件包括子智能体生成、委托、通信、工具使用、返回、聚合和停止决策。使用这个镜头，我们确定了三个技术轴。首先，奖励设计涵盖八个系列，包括针对并行加速、分割正确性和聚合质量的编排奖励。其次，奖励和信用信号附加到...</p>
    <p class="daily-abstract"><strong>Abstract:</strong> As large language model (LLM) agents evolve from isolated tool users into coordinated teams, reinforcement learning (RL) must optimize not only individual actions but also how work is spawned, delegated, communicated, ag...</p>
  </div>
</div>
<div class="daily-paper-card">
  <a href="entities/papers/2605-02789v1-funfuzz-an-llm-powered-evolutionary-fuzzing-framew.html" class="daily-thumb"><img src="assets/papers/2605-02789v1/fig1.png" alt="FunFuzz: An LLM-Powered Evolutionary Fuzzing Framework"></a>
  <div class="daily-paper-body">
    <h3><a href="entities/papers/2605-02789v1-funfuzz-an-llm-powered-evolutionary-fuzzing-framew.html">FunFuzz: An LLM-Powered Evolutionary Fuzzing Framework</a></h3>
    <div class="daily-meta">2026-05-04 · cs.CR, cs.CL · 大语言模型</div>
    <p><strong>方法/亮点：</strong>We present FunFuzz, a multi-island evolutionary fuzzing framework that runs several isolated searches in parallel and periodically migrates high-value candidates to maintain diversity.</p>
    <p class="daily-abstract"><strong>摘要（中文）：</strong>中文摘要暂未生成。</p>
    <p class="daily-abstract"><strong>Abstract:</strong> Modern fuzzers increasingly use Large Language Models (LLMs) to generate structured inputs, but LLM-driven fuzzing is sensitive to prompt initialization and sampling variance, which can reduce exploration efficiency and ...</p>
  </div>
</div>
<div class="daily-paper-card">
  
  <div class="daily-paper-body">
    <h3><a href="entities/papers/2605-02782v1-when-audio-language-models-fail-to-leverage-multim.html">When Audio-Language Models Fail to Leverage Multimodal Context for Dysarthric Speech Recognition</a></h3>
    <div class="daily-meta">2026-05-04 · cs.AI, cs.CL, eess.AS · 大语言模型 / 多模态学习 / 基准评估 / 医学AI</div>
    <p><strong>方法/亮点：</strong>We introduce a benchmark built on the Speech Accessibility Project (SAP) dataset that tests whether diagnosis labels, clinician-derived speech ratings, and progressively richer clinical descriptions improve transcription accuracy for dysart</p>
    <p class="daily-abstract"><strong>摘要（中文）：</strong>自动语音识别（ASR）系统对于构音障碍和其他非典型语音仍然很脆弱。最近的音频语言模型提高了通过在推理时调节额外的临床背景来提高性能的可能性，但尚不清楚这些模型是否可以利用这些信息。我们引入了一个基于语音无障碍项目 (SAP) 数据集的基准，该基准测试诊断标签、临床医生得出的语音评级以及逐渐丰富的临床描述是否可以提高构音障碍语音的转录准确性。通过对九个模型的匹配比较，我们发现当前模型并没有有意义地使用这种上下文：诊断信息和临床详细的提示产...</p>
    <p class="daily-abstract"><strong>Abstract:</strong> Automatic speech recognition (ASR) systems remain brittle on dysarthric and other atypical speech. Recent audio-language models raise the possibility of improving performance by conditioning on additional clinical contex...</p>
  </div>
</div>
<div class="daily-paper-card">
  <a href="entities/papers/2605-02751v1-mitigating-misalignment-contagion-by-steering-with.html" class="daily-thumb"><img src="assets/papers/2605-02751v1/fig1.png" alt="Mitigating Misalignment Contagion by Steering with Implicit Traits"></a>
  <div class="daily-paper-body">
    <h3><a href="entities/papers/2605-02751v1-mitigating-misalignment-contagion-by-steering-with.html">Mitigating Misalignment Contagion by Steering with Implicit Traits</a></h3>
    <div class="daily-meta">2026-05-04 · cs.AI, cs.CL · 大语言模型 / AI安全与对齐 / 智能体</div>
    <p><strong>方法/亮点：</strong>Instead, we propose steering with implicit traits: a technique that intermittently injects system prompts with statements that reinforce an LMs initial traits and is more effective than system prompt repetition at keeping models in line wit</p>
    <p class="daily-abstract"><strong>摘要（中文）：</strong>语言模型 (LM) 越来越多地用于高风险、多代理环境，在这些环境中，遵循指令和保持价值一致性至关重要。大多数对齐研究都集中在单个 LM 和单个用户之间的交互，未能解决多轮交互中多个 LM 之间错位行为传播的风险。当多个语言模型参与多回合对话式社交困境游戏时，我们在多个语言模型中发现了这种现象的证据，我们将这种现象称为错位传染。具体来说，我们发现 LM 在游戏结束后变得更加反社会，并且当其他玩家被引导进行恶意行为时，这种影响会加剧。我们探...</p>
    <p class="daily-abstract"><strong>Abstract:</strong> Language models (LMs) are increasingly used in high-stakes, multi-agent settings, where following instructions and maintaining value alignment are critical. Most alignment research focuses on interactions between a singl...</p>
  </div>
</div>
<div class="daily-paper-card">
  <a href="entities/papers/2605-02740v1-foundation-models-to-unlock-real-world-evidence-fr.html" class="daily-thumb"><img src="assets/papers/2605-02740v1/fig1.png" alt="Foundation Models to Unlock Real-World Evidence from Nationwide Medical Claims"></a>
  <div class="daily-paper-body">
    <h3><a href="entities/papers/2605-02740v1-foundation-models-to-unlock-real-world-evidence-fr.html">Foundation Models to Unlock Real-World Evidence from Nationwide Medical Claims</a></h3>
    <div class="daily-meta">2026-05-04 · cs.AI, cs.CL · 大语言模型 / 基准评估 / 医学AI</div>
    <p><strong>方法/亮点：</strong>Here we present ReClaim, a generative transformer trained from scratch on 43.8 billion medical events from more than 200 million enrollees in the MarketScan claims data spanning 2008-2022.</p>
    <p class="daily-abstract"><strong>摘要（中文）：</strong>来自大规模现实世界数据 (RWD) 的证据越来越多地为监管评估和医疗保健决策提供信息。行政索赔提供了人口规模的医疗保健利用、支出的纵向记录以及诊断、程序和药物的详细编码，但它们作为医疗保健基础模型基础的潜力在很大程度上仍未被开发。在这里，我们介绍 ReClaim，这是一个生成转换器，它根据 2008 年至 2022 年 MarketScan 索赔数据中超过 2 亿名参与者的 438 亿个医疗事件进行了训练。 ReClaim 对诊断、手术...</p>
    <p class="daily-abstract"><strong>Abstract:</strong> Evidence derived from large-scale real-world data (RWD) is increasingly informing regulatory evaluation and healthcare decision-making. Administrative claims provide population-scale, longitudinal records of healthcare u...</p>
  </div>
</div>
<div class="daily-paper-card">
  <a href="entities/papers/2605-02720v1-pubmed-ophtha-an-open-resource-for-training-ophtha.html" class="daily-thumb"><img src="assets/papers/2605-02720v1/fig1.png" alt="PubMed-Ophtha: An open resource for training ophthalmology vision-language models on scientific literature"></a>
  <div class="daily-paper-body">
    <h3><a href="entities/papers/2605-02720v1-pubmed-ophtha-an-open-resource-for-training-ophtha.html">PubMed-Ophtha: An open resource for training ophthalmology vision-language models on scientific literature</a></h3>
    <div class="daily-meta">2026-05-04 · cs.CV, cs.CL · 大语言模型 / 多模态学习 / 基准评估 / 图神经网络</div>
    <p><strong>方法/亮点：</strong>We present PubMed-Ophtha, a hierarchical dataset of 102,023 ophthalmological image-caption pairs extracted from 15,842 open-access articles in PubMed Central.</p>
    <p class="daily-abstract"><strong>摘要（中文）：</strong>视觉语言模型为眼科带来了巨大的希望，但其发展依赖于仍然稀缺的大规模、高质量的图像文本数据集。我们提出了 PubMed-Ophtha，这是一个从 PubMed Central 的 15,842 篇开放获取文章中提取的 102,023 个眼科图像标题对的分层数据集。与现有数据集不同，图表是直接从全分辨率文章 PDF 中提取的，并分解为其组成面板、面板标识符和单个图像。每个图像都用其成像方式（彩色眼底摄影、光学相干断层扫描、视网膜成像或其他）...</p>
    <p class="daily-abstract"><strong>Abstract:</strong> Vision-language models hold considerable promise for ophthalmology, but their development depends on large-scale, high-quality image-text datasets that remain scarce. We present PubMed-Ophtha, a hierarchical dataset of 1...</p>
  </div>
</div>
<div class="daily-paper-card">
  <a href="entities/papers/2605-02892v1-albumfill-album-guided-reasoning-and-retrieval-for.html" class="daily-thumb"><img src="assets/papers/2605-02892v1/fig1.png" alt="AlbumFill: Album-Guided Reasoning and Retrieval for Personalized Image Completion"></a>
  <div class="daily-paper-body">
    <h3><a href="entities/papers/2605-02892v1-albumfill-album-guided-reasoning-and-retrieval-for.html">AlbumFill: Album-Guided Reasoning and Retrieval for Personalized Image Completion</a></h3>
    <div class="daily-meta">2026-05-04 · cs.CV, cs.IR · 大语言模型 / 多模态学习 / 基准评估</div>
    <p><strong>方法/亮点：</strong>We present AlbumFill, a training-free framework that retrieves identity-consistent references from personal albums for personalized completion.</p>
    <p class="daily-abstract"><strong>摘要（中文）：</strong>个性化图像补全旨在恢复个人照片中的遮挡区域，同时保留身份和外观。现有方法要么依赖于通常无法保持身份一致性的通用修复模型，要么假设明确提供了合适的参考图像。在实践中，通常不会明确提供合适的参考，从而要求系统在个人照片集中搜索身份一致的图像。我们提出了 AlbumFill，这是一个免培训的框架，可以从个人相册中检索身份一致的参考以进行个性化完成。给定一个被遮挡的图像和一个个人相册，视觉语言模型会推断缺失的语义线索来指导组合图像检索，并且检索...</p>
    <p class="daily-abstract"><strong>Abstract:</strong> Personalized image completion aims to restore occluded regions in personal photos while preserving identity and appearance. Existing methods either rely on generic inpainting models that often fail to maintain identity c...</p>
  </div>
</div>
<div class="daily-paper-card">
  <a href="entities/papers/2605-02866v1-laplacian-frequency-interaction-network-for-rural.html" class="daily-thumb"><img src="assets/papers/2605-02866v1/fig1.png" alt="Laplacian Frequency Interaction Network for Rural Thematic Road Extraction"></a>
  <div class="daily-paper-body">
    <h3><a href="entities/papers/2605-02866v1-laplacian-frequency-interaction-network-for-rural.html">Laplacian Frequency Interaction Network for Rural Thematic Road Extraction</a></h3>
    <div class="daily-meta">2026-05-04 · cs.CV · 大语言模型 / 多模态学习 / 基准评估 / 自动驾驶</div>
    <p><strong>方法/亮点：</strong>To address these challenges, we propose LFINet, a Laplacian Frequency Interaction Network.</p>
    <p class="daily-abstract"><strong>摘要（中文）：</strong>农村专题路网建设旨在从农机运动轨迹图像中提取拓扑道路结构。然而，这项任务面临着挑战，现有研究中常用的下采样方法往往会模糊稀疏的高频道路结构，而密集现场操作产生的重噪声往往会导致提取的网络中出现碎片或冗余拓扑。为了应对这些挑战，我们提出了 LFINet，一种拉普拉斯频率交互网络。该网络从拉普拉斯多尺度分离器（LMS）开始，将图像解耦为低频语义上下文和高频结构细节。然后，跨频率交互模块 (CFIB) 通过双通道架构处理这些组件，其中高频模块...</p>
    <p class="daily-abstract"><strong>Abstract:</strong> Rural thematic road network construction aims to extract topological road structures from movement trajectory images of agricultural machinery. However, this task faces challenges where downsampling methods commonly used...</p>
  </div>
</div>
</div>

---

## 🧭 知识导航

### 核心概念

| 概念 | 说明 | 论文数 |
|------|------|--------|
| [大语言模型](concepts/large-language-model.html) | GPT、LLaMA 等大规模预训练语言模型 | 8 |
| [强化学习](concepts/reinforcement-learning.html) | RLHF、RLVR、DPO、GRPO 等对齐技术 | 2 |
| [多模态学习](concepts/multimodal-learning.html) | 视觉-语言模型、跨模态推理 | 2 |
| [知识蒸馏](concepts/knowledge-distillation.html) | 教师-学生框架、黑箱蒸馏、策略蒸馏 | 1 |
| [世界模型](concepts/world-models.html) | 环境动态预测与生成 | 1 |
| [基准评估](concepts/benchmarking.html) | 标准化测试与评估方法论 | 2 |
| [智能体](concepts/ai-agents.html) | LLM 驱动的自主代理与多代理协作 | 8 |
| [图神经网络](concepts/graph-neural-networks.html) | 图结构学习与推理 | 1 |
| [自动驾驶](concepts/autonomous-driving.html) | 感知、预测、规划与世界模型 | 1 |
| [AI安全与对齐](concepts/ai-safety-alignment.html) | 对齐问题、对抗训练、安全评估 | 2 |

### 技术方向

- **训练方法** → [强化学习](concepts/reinforcement-learning.html) | [知识蒸馏](concepts/knowledge-distillation.html)
- **模型架构** → [大语言模型](concepts/large-language-model.html) | [图神经网络](concepts/graph-neural-networks.html) | [世界模型](concepts/world-models.html)
- **应用场景** → [自动驾驶](concepts/autonomous-driving.html) | [医学AI](concepts/medical-ai.html) | [智能体](concepts/ai-agents.html)
- **评估与安全** → [基准评估](concepts/benchmarking.html) | [AI安全与对齐](concepts/ai-safety-alignment.html)
