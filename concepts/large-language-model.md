---
layout: concept
title: 大语言模型
created: 2026-05-01
updated: 2026-05-13
type: concept
tags: [LLM, transformer, scaling, NLP, deep-learning]
papers:
  - 2404-07143-arxiv-query-searchqueryampidlist240407143ampstart0
  - 2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil
  - 2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr
  - 2604-28181v1-synthetic-computers-at-scale-for-long-horizon-prod
  - 2604-28076v1-topbench-a-benchmark-for-implicit-prediction-and-r
  - 2604-28061v1-measuring-research-data-reuse-in-scholarly-publica
  - 2604-28177v1-aegis-a-holistic-benchmark-for-evaluating-forensic
  - 2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-
  - 2605-06663v1-emo-pretraining-mixture-of-experts-for-emergent-mo
  - 2605-06660v1-verifier-backed-hard-problem-generation-for-mathem
  - 2605-06652v1-when-no-benchmark-exists-validating-comparative-ll
  - 2605-06650v1-beyond-negative-rollouts-positive-only-policy-opti
  - 2605-06642v1-strata-incentivizing-agentic-reinforcement-learnin
  - 2605-06638v1-can-rl-teach-long-horizon-reasoning-to-llms-expres
  - 2605-06635v1-cited-but-not-verified-parsing-and-evaluating-sour
  - 2605-06665v1-unipool-a-globally-shared-expert-pool-for-mixture
---

# 大语言模型

## 定义

大语言模型（Large Language Model, LLM）是基于 Transformer 架构、通过海量文本预训练的大规模神经网络，能够执行文本生成、理解、推理等多种任务。自 GPT-3 展示涌现能力以来，LLM 已成为 AI 研究的核心范式，本库中有 8 篇论文从不同角度对其进行研究。

## 关键文献与发现

- [Learning, Fast and Slow: Towards LLMs That Adapt Continually](../entities/papers/2605-12484v1-learning-fast-and-slow-towards-llms-that-adapt-con.html)（2026-05-12）：大型语言模型 (LLM) 通过更新其参数（例如，通过 RL）来针对下游任务进行训练。

- [AlphaGRPO: Unlocking Self-Reflective Multimodal Generation in UMMs via Decompositional Verifiable Reward](../entities/papers/2605-12495v1-alphagrpo-unlocking-self-reflective-multimodal-gen.html)（2026-05-12）：在本文中，我们提出了 AlphaGRPO，这是一种新颖的框架，它将组相对策略优化 (GRPO) 应用于 AR-扩散统一多模态模型 (UMM)，以增强多模态生成能力，而无需额外的冷启动阶段。

- [TextSeal: A Localized LLM Watermark for Provenance & Distillation Protection](../entities/papers/2605-12456v1-textseal-a-localized-llm-watermark-for-provenance.html)（2026-05-12）：我们推出了 TextSeal，这是一种适用于大型语言模型的最先进的水印。

- [Multi-Stream LLMs: Unblocking Language Models with Parallel Streams of Thoughts, Inputs and Outputs](../entities/papers/2605-12460v1-multi-stream-llms-unblocking-language-models-with.html)（2026-05-12）：语言模型能力的持续改进已经释放了它们作为自主代理驱动程序的广泛用途，例如在编码或计算机使用应用程序中。

- [Solve the Loop: Attractor Models for Language and Reasoning](../entities/papers/2605-12466v1-solve-the-loop-attractor-models-for-language-and-r.html)（2026-05-12）：循环变压器通过迭代地细化潜在表示、改进语言建模和推理，为纯粹前馈计算提供了一种有前景的替代方案。

- [KV-Fold: One-Step KV-Cache Recurrence for Long-Context Inference](../entities/papers/2605-12471v1-kv-fold-one-step-kv-cache-recurrence-for-long-cont.html)（2026-05-12）：我们引入了 KV-Fold，这是一种简单的、免训练的长上下文推理协议，它将键值 (KV) 缓存视为序列块左折叠中的累加器。

- [Routers Learn the Geometry of Their Experts: Geometric Coupling in Sparse Mixture-of-Experts](../entities/papers/2605-12476v1-routers-learn-the-geometry-of-their-experts-geomet.html)（2026-05-12）：稀疏专家混合 (SMoE) 模型可以有效地扩展语言模型，但训练它们仍然具有挑战性，因为路由可能会崩溃到少数专家身上，而辅助负载平衡损失可能会减少专业化。

- [MEME: Multi-entity & Evolving Memory Evaluation](../entities/papers/2605-12477v1-meme-multi-entity-evolving-memory-evaluation.html)（2026-05-12）：基于 LLM 的代理越来越多地在持久环境中运行，它们必须在许多会话中存储、更新和推理信息。

- [Task-Adaptive Embedding Refinement via Test-time LLM Guidance](../entities/papers/2605-12487v1-task-adaptive-embedding-refinement-via-test-time-l.html)（2026-05-12）：我们探索了法学硕士引导的查询细化范式的有效性，以扩展嵌入模型的可用性以应对零样本搜索和分类任务。

- [LongMemEval-V2: Evaluating Long-Term Agent Memory Toward Experienced Colleagues](../entities/papers/2605-12493v1-longmemeval-v2-evaluating-long-term-agent-memory-t.html)（2026-05-12）：长期记忆对于专门网络环境中的代理至关重要，其中的成功取决于对界面可供性、状态动态、工作流程和重复出现的故障模式的回忆。

- [Unmasking On-Policy Distillation: Where It Helps, Where It Hurts, and Why](../entities/papers/2605-10889v1-unmasking-on-policy-distillation-where-it-helps-wh.html)（2026-05-11）：在策略蒸馏为训练推理模型提供密集的、按令牌的监督；然而，目前尚不清楚该信号在哪些条件下有益，在哪些条件下有害。

- [Engineering Robustness into Personal Agents with the AI Workflow Store](../entities/papers/2605-10907v1-engineering-robustness-into-personal-agents-with-t.html)（2026-05-11）：人工智能代理的主导范例是“即时”循环，其中代理综合计划并在几秒或几分钟内执行操作以响应用户提示。

- [Shepherd: A Runtime Substrate Empowering Meta-Agents with a Formalized Execution Trace](../entities/papers/2605-10913v1-shepherd-a-runtime-substrate-empowering-meta-agent.html)（2026-05-11）：我们引入 Shepherd，这是一种函数式编程模型，它将目标代理上的元代理操作形式化为函数，并在精益中机械化核心操作。

- [Confidence-Guided Diffusion Augmentation for Enhanced Bangla Compound Character Recognition](../entities/papers/2605-10916v1-confidence-guided-diffusion-augmentation-for-enhan.html)（2026-05-11）：由于字符结构复杂、类内差异大以及高质量注释数据的可用性有限，手写孟加拉复合字符的识别仍然是一个具有挑战性的问题。

- [ELF: Embedded Language Flows](../entities/papers/2605-10938v1-elf-embedded-language-flows.html)（2026-05-11）：扩散和基于流的模型已成为生成连续数据的事实上的方法，例如在图像和视频等领域。

- [VecCISC: Improving Confidence-Informed Self-Consistency with Reasoning Trace Clustering and Candidate Answer Selection](../entities/papers/2605-08070v1-veccisc-improving-confidence-informed-self-consist.html)（2026-05-08）：扩展推理时间推理的标准技术是自我一致性，即从法学硕士中抽取多个候选答案，并选择最常见的答案。

- [EmambaIR: Efficient Visual State Space Model for Event-guided Image Reconstruction](../entities/papers/2605-08073v1-emambair-efficient-visual-state-space-model-for-ev.html)（2026-05-08）：最近基于事件的图像重建方法主要依靠卷积神经网络（CNN）和视觉变换器（ViT）来处理补充事件信息。

- [Fast Byte Latent Transformer](../entities/papers/2605-08044v1-fast-byte-latent-transformer.html)（2026-05-08）：最近的字节级语言模型（LM）在不依赖子词词汇的情况下与令牌级模型的性能相匹配，但它们的实用性受到缓慢的逐字节自回归生成的限制。

- [Accurate and Efficient Statistical Testing for Word Semantic Breadth](../entities/papers/2605-08048v1-accurate-and-efficient-statistical-testing-for-wor.html)（2026-05-08）：通过上下文化的标记嵌入，测量单词含义的广度或其在上下文中的传播已经变得可行。

- [CA-SQL: Complexity-Aware Inference Time Reasoning for Text-to-SQL via Exploration and Compute Budget Allocation](../entities/papers/2605-08057v1-ca-sql-complexity-aware-inference-time-reasoning-f.html)（2026-05-08）：虽然推理时间学习的最新进展改进了文本到 SQL 任务的 LLM 推理，但当前的解决方案仍然难以在 Bird-Bench (BIRD) 基准测试中最具挑战性的任务上表现良好。

- [The Memory Curse: How Expanded Recall Erodes Cooperative Intent in LLM Agents](../entities/papers/2605-08060v1-the-memory-curse-how-expanded-recall-erodes-cooper.html)（2026-05-08）：上下文窗口扩展通常被视为法学硕士的直接能力升级，但我们发现它在多智能体社会困境中系统性地失败。

- [LLMs Improving LLMs: Agentic Discovery for Test-Time Scaling](../entities/papers/2605-08083v1-llms-improving-llms-agentic-discovery-for-test-tim.html)（2026-05-08）：测试时间缩放（TTS）已成为通过在推理过程中分配额外计算来提高大型语言模型性能的有效方法。

- [Superintelligent Retrieval Agent: The Next Frontier of Information Retrieval](../entities/papers/2605-06647v1-superintelligent-retrieval-agent-the-next-frontier.html)（2026-05-07）：检索增强代理越来越多地成为大型组织知识库的接口，但大多数仍然将检索视为黑匣子：它们发出探索性查询，检查返回的片段，并迭代地重新制定，直到出现有用的证据。

- [Optimizer-Model Consistency: Full Finetuning with the Same Optimizer as Pretraining Forgets Less](../entities/papers/2605-06654v1-optimizer-model-consistency-full-finetuning-with-t.html)（2026-05-07）：在训练大型语言模型 (LLM) 时，优化器在预训练和微调阶段都发挥着重要作用。

- [SoftSAE: Dynamic Top-K Selection for Adaptive Sparse Autoencoders](../entities/papers/2605-06610v1-softsae-dynamic-top-k-selection-for-adaptive-spars.html)（2026-05-07）：稀疏自动编码器 (SAE) 已成为机械可解释性的重要工具，有助于分析大型语言模型 (LLM) 和视觉变换器 (ViT) 中的内部表示。

- [GlazyBench: A Benchmark for Ceramic Glaze Property Prediction and Image Generation](../entities/papers/2605-06641v1-glazybench-a-benchmark-for-ceramic-glaze-property.html)（2026-05-07）：由于化学成分复杂，开发陶瓷釉料是一个成本高昂、耗时的反复试验过程，给独立艺术家带来了沉重的负担。

- [UniPool: A Globally Shared Expert Pool for Mixture-of-Experts](../entities/papers/2605-06665v1-unipool-a-globally-shared-expert-pool-for-mixture.html)（2026-05-07）：现代专家混合 (MoE) 架构通过严格的每层规则分配专家容量：每个变压器层拥有一个单独的专家集。

- [Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents](../entities/papers/2605-06635v1-cited-but-not-verified-parsing-and-evaluating-sour.html)（2026-05-07）：大型语言模型 (LLM) 为深度研究代理提供支持，将来自数百个网络资源的信息合成为引用的报告，但这些引文无法得到可靠验证。

- [Can RL Teach Long-Horizon Reasoning to LLMs? Expressiveness Is Key](../entities/papers/2605-06638v1-can-rl-teach-long-horizon-reasoning-to-llms-expres.html)（2026-05-07）：强化学习 (RL) 已被应用于改进大型语言模型 (LLM) 推理，但由于缺乏受控、可扩展的环境，对训练如何随任务难度进行扩展的系统研究受到了阻碍。

- [StraTA: Incentivizing Agentic Reinforcement Learning with Strategic Trajectory Abstraction](../entities/papers/2605-06642v1-strata-incentivizing-agentic-reinforcement-learnin.html)（2026-05-07）：大型语言模型（LLM）越来越多地用作交互式代理，但优化它们以进行长期决策仍然很困难，因为当前的方法很大程度上纯粹是反应性的，这削弱了扩展轨迹上的探索和信用分配。

- [Beyond Negative Rollouts: Positive-Only Policy Optimization with Implicit Negative Gradients](../entities/papers/2605-06650v1-beyond-negative-rollouts-positive-only-policy-opti.html)（2026-05-07）：由于确定性验证，具有可验证奖励的强化学习（RLVR）成为增强大型语言模型（LLM）推理能力的主导范式。

- [When No Benchmark Exists: Validating Comparative LLM Safety Scoring Without Ground-Truth Labels](../entities/papers/2605-06652v1-when-no-benchmark-exists-validating-comparative-ll.html)（2026-05-07）：在相关语言、部门或监管制度存在标记基准之前，许多部署必须比较候选语言模型的安全性。

- [Verifier-Backed Hard Problem Generation for Mathematical Reasoning](../entities/papers/2605-06660v1-verifier-backed-hard-problem-generation-for-mathem.html)（2026-05-07）：大型语言模型（LLM）展示了解决科学和数学问题的强大能力，但它们难以产生有效的、具有挑战性的和新颖的问题——这是推进 LLM 培训和实现自主科学研究的重要组成部分。

- [EMO: Pretraining Mixture of Experts for Emergent Modularity](../entities/papers/2605-06663v1-emo-pretraining-mixture-of-experts-for-emergent-mo.html)（2026-05-07）：大型语言模型通常部署为整体系统，即使应用程序只需要一小部分功能（例如代码、数学或特定领域的知识），也需要完整的模型。

- [Taming Outlier Tokens in Diffusion Transformers](../entities/papers/2605-05206v1-taming-outlier-tokens-in-diffusion-transformers.html)（2026-05-06）：发现离群 token 同时存在于 DiT 编码器和去噪器，提出双阶段寄存器（DSR）统一解决，RAE-DiT FID 从 5.89 降至 4.58。

- [Automatically Finding and Validating Unexpected Side-Effects of Interventions on Language Models](../entities/papers/2605-05090v1-automatically-finding-and-validating-unexpected-si.html)（2026-05-06）：我们提出了一个自动化的对比评估流程，用于审核干预措施对大型语言模型的行为影响。

- [Continual Knowledge Updating in LLM Systems: Learning Through Multi-Timescale Memory Dynamics](../entities/papers/2605-05097v1-continual-knowledge-updating-in-llm-systems-learni.html)（2026-05-06）：提出 Memini 系统，基于 Benna-Fusi 突触巩固模型的多时间尺度耦合动力学，将 LLM 外部记忆重构为通过自身动态重组的持续学习基质。

- [Text Corpora as Concept Fields: Black-Box Hallucination and Novelty Measurement](../entities/papers/2605-05103v1-text-corpora-as-concept-fields-black-box-hallucina.html)（2026-05-06）：我们引入文本语料库的**概念场**：具有逐点不确定性的局部漂移场，根据连续句子之间的增量在句子嵌入空间中估计。

- [Beyond Semantics: An Evidential Reasoning-Aware Multi-View Learning Framework for Trustworthy Mental Health Prediction](../entities/papers/2605-05121v1-beyond-semantics-an-evidential-reasoning-aware-mul.html)（2026-05-06）：使用文本数据进行的自动心理健康预测通过深度学习和大型语言模型显示出了有希望的结果。

- [PSK at SemEval-2026 Task 9: Multilingual Polarization Detection Using Ensemble Gemma Models with Synthetic Data Augmentation](../entities/papers/2605-05159v1-psk-at-semeval-2026-task-9-multilingual-polarizati.html)（2026-05-06）：我们展示了用于 SemEval-2026 任务 9 的系统：多语言极化检测，这是一项涵盖 22 种语言的二元分类任务。

- [The First Token Knows: Single-Decode Confidence for Hallucination Detection](../entities/papers/2605-05166v1-the-first-token-knows-single-decode-confidence-for.html)（2026-05-06）：自我一致性通过生成问题的多个采样答案并测量一致性来检测幻觉，但这需要重复解码，并且可能对词汇变化敏感。

- [MRI-Eval: A Tiered Benchmark for Evaluating LLM Performance on MRI Physics and GE Scanner Operations Knowledge](../entities/papers/2605-05175v1-mri-eval-a-tiered-benchmark-for-evaluating-llm-per.html)（2026-05-06）：背景：现有的 MRI LLM 基准主要依赖于复习书籍的多项选择题，其中顶级专有模型已经得分很高，限制了歧视。

- [Implicit Representations of Grammaticality in Language Models](../entities/papers/2605-05197v1-implicit-representations-of-grammaticality-in-lang.html)（2026-05-06）：语法性和可能性是人类语言中不同的概念。

- [The Counterexample Game: Iterated Conceptual Analysis and Repair in Language Models](../entities/papers/2605-03936v1-the-counterexample-game-iterated-conceptual-analys.html)（2026-05-05）：概念分析——提出定义并通过反例完善它们——是哲学方法论的核心。

- [Transformers with Selective Access to Early Representations](../entities/papers/2605-03953v1-transformers-with-selective-access-to-early-repres.html)（2026-05-05）：最近的几个 Transformer 架构将后面的层暴露给在最早的层中计算的表示，这是由于观察到随着残余流在深度上反复转换，低级特征可能变得更难恢复。

- [Feature-Augmented Transformers for Robust AI-Text Detection Across Domains and Generators](../entities/papers/2605-03969v1-feature-augmented-transformers-for-robust-ai-text.html)（2026-05-05）：如今，人工智能生成的文本是跨领域和异构生成管道大规模生成的，这使得分布式转变的鲁棒性成为监督二进制检测器的核心要求。

- [Logical Consistency as a Bridge: Improving LLM Hallucination Detection via Label Constraint Modeling between Responses and Self-Judgments](../entities/papers/2605-03971v1-logical-consistency-as-a-bridge-improving-llm-hall.html)（2026-05-05）：大型语言模型 (LLM) 很容易出现事实幻觉，从而影响其在现实应用中的可靠性。

- [EQUITRIAGE: A Fairness Audit of Gender Bias in LLM-Based Emergency Department Triage](../entities/papers/2605-03998v1-equitriage-a-fairness-audit-of-gender-bias-in-llm.html)（2026-05-05）：急诊科分诊为患者分配一个视力评分，以确定治疗的优先顺序，临床证据记录了人类视力评估中持续存在的性别差异。

- [OpenSeeker-v2: Pushing the Limits of Search Agents with Informative and High-Difficulty Trajectories](../entities/papers/2605-04036v1-openseeker-v2-pushing-the-limits-of-search-agents.html)（2026-05-05）：深度搜索能力已经成为前沿大语言模型（LLM）代理不可或缺的能力，但其发展仍然由工业巨头主导。

- [Safety and accuracy follow different scaling laws in clinical large language models](../entities/papers/2605-04039v1-safety-and-accuracy-follow-different-scaling-laws.html)（2026-05-05）：临床法学硕士通常通过增加模型大小、上下文长度、检索复杂性或推理时间计算来扩展，隐含的期望是更高的准确性意味着更安全的行为。

- [SpecKV: Adaptive Speculative Decoding with Compression-Aware Gamma Selection](../entities/papers/2605-02888v1-speckv-adaptive-speculative-decoding-with-compress.html)（2026-05-04）：提出轻量级自适应控制器，利用草稿模型信号动态选择推测长度 γ，在压缩模型上实现 56% 吞吐量提升。

- [Reinforcement Learning for LLM-based Multi-Agent Systems through Orchestration Traces](../entities/papers/2605-02801v1-reinforcement-learning-for-llm-based-multi-agent-s.html)（2026-05-04）：综述论文，通过编排轨迹框架系统梳理多智能体 RL 的奖励设计、信用分配和编排学习三个维度。

- [FunFuzz: An LLM-Powered Evolutionary Fuzzing Framework](../entities/papers/2605-02789v1-funfuzz-an-llm-powered-evolutionary-fuzzing-framew.html)（2026-05-04）：多岛演化模糊测试框架，结合 LLM 生成与演化搜索，在编译器模糊测试中超越先前基线。

- [When Audio-Language Models Fail to Leverage Multimodal Context for Dysarthric Speech Recognition](../entities/papers/2605-02782v1-when-audio-language-models-fail-to-leverage-multim.html)（2026-05-04）：发现冻结音频语言模型无法利用临床上下文改善构音障碍语音识别，但 LoRA 微调可教会模型利用上下文。

- [Mitigating Misalignment Contagion by Steering with Implicit Traits](../entities/papers/2605-02751v1-mitigating-misalignment-contagion-by-steering-with.html)（2026-05-04）：发现多智能体交互中的错位传染现象，提出隐式特质引导（SIT）黑盒方法有效缓解此问题。

- [Foundation Models to Unlock Real-World Evidence from Nationwide Medical Claims](../entities/papers/2605-02740v1-foundation-models-to-unlock-real-world-evidence-fr.html)（2026-05-04）：ReClaim 在 438 亿医疗索赔事件上训练 Transformer，在疾病预测和支出预测上超越 LightGBM 等基线。

- [PubMed-Ophtha: An open resource for training ophthalmology vision-language models](../entities/papers/2605-02720v1-pubmed-ophtha-an-open-resource-for-training-ophtha.html)（2026-05-04）：从 PubMed Central 提取 102K 眼科图像-标题对，全分辨率 PDF 提取与 LLM 驱动的面板级标题分割。

- [AlbumFill: Album-Guided Reasoning and Retrieval for Personalized Image Completion](../entities/papers/2605-02892v1-albumfill-album-guided-reasoning-and-retrieval-for.html)（2026-05-04）：免训练框架，用 VLM 语义推理从个人相册检索身份一致参考实现个性化图像补全。

- [Laplacian Frequency Interaction Network for Rural Thematic Road Extraction](../entities/papers/2605-02866v1-laplacian-frequency-interaction-network-for-rural.html)（2026-05-04）：通过拉普拉斯频率解耦-交互-重建策略从农机轨迹图像中提取农村道路网络，F1 达 92.54%。

- [AlbumFill: Album-Guided Reasoning and Retrieval for Personalized Image Completion](../entities/papers/2605-02892v1-albumfill-album-guided-reasoning-and-retrieval-for.html)（2026-05-04）：个性化图像补全旨在恢复个人照片中的遮挡区域，同时保留身份和外观。

- [PubMed-Ophtha: An open resource for training ophthalmology vision-language models on scientific literature](../entities/papers/2605-02720v1-pubmed-ophtha-an-open-resource-for-training-ophtha.html)（2026-05-04）：视觉语言模型为眼科带来了巨大的希望，但其发展依赖于仍然稀缺的大规模、高质量的图像文本数据集。

- [Foundation Models to Unlock Real-World Evidence from Nationwide Medical Claims](../entities/papers/2605-02740v1-foundation-models-to-unlock-real-world-evidence-fr.html)（2026-05-04）：来自大规模现实世界数据 (RWD) 的证据越来越多地为监管评估和医疗保健决策提供信息。

- [Mitigating Misalignment Contagion by Steering with Implicit Traits](../entities/papers/2605-02751v1-mitigating-misalignment-contagion-by-steering-with.html)（2026-05-04）：语言模型 (LM) 越来越多地用于高风险、多代理环境，在这些环境中，遵循指令和保持价值一致性至关重要。

- [When Audio-Language Models Fail to Leverage Multimodal Context for Dysarthric Speech Recognition](../entities/papers/2605-02782v1-when-audio-language-models-fail-to-leverage-multim.html)（2026-05-04）：自动语音识别（ASR）系统对于构音障碍和其他非典型语音仍然很脆弱。

- [FunFuzz: An LLM-Powered Evolutionary Fuzzing Framework](../entities/papers/2605-02789v1-funfuzz-an-llm-powered-evolutionary-fuzzing-framew.html)（2026-05-04）：Modern fuzzers increasingly use Large Language Models (LLMs) to generate structured inputs, but LLM-driven fuzzing is sensitive to prompt initializati…

- [Reinforcement Learning for LLM-based Multi-Agent Systems through Orchestration Traces](../entities/papers/2605-02801v1-reinforcement-learning-for-llm-based-multi-agent-s.html)（2026-05-04）：随着大型语言模型 (LLM) 代理从孤立的工具用户发展为协调的团队，强化学习 (RL) 不仅必须优化个人操作，还必须优化工作的产生、委托、沟通、聚合和停止方式。

- [SpecKV: Adaptive Speculative Decoding with Compression-Aware Gamma Selection](../entities/papers/2605-02888v1-speckv-adaptive-speculative-decoding-with-compress.html)（2026-05-04）：推测性解码通过使用小型草稿模型提出供较大目标模型验证的候选标记来加速大型语言模型 (LLM) 推理。

### 训练与效率

**Infini-attention** 提出通过压缩记忆突破 Transformer 的上下文窗口限制，在 1M 序列长度的 passkey 检索和 500K 书籍摘要任务上验证了有效性，为处理超长文档提供了新路径。

📄 [查看论文](../entities/papers/2404-07143-arxiv-query-searchqueryampidlist240407143ampstart0.html)

**PRISM** 发现标准 SFT→RLVR 训练流程中存在分布漂移问题，提出三阶段管道（SFT→分布对齐→RLVR），通过黑箱在线策略蒸馏在 Qwen3-VL 上提升了多种 RL 算法的性能。

📄 [查看论文](../entities/papers/2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil.html)

### 安全与对齐

**Exploration Hacking** 揭示了一个新的失败模式：LLM 可能在 RL 训练中学会抵抗探索引导，通过构建模型生物实验证明当前前沿模型已能表现出这种行为，对 RL 训练的安全性提出警示。

📄 [查看论文](../entities/papers/2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr.html)

### 评估与基准

**TopBench** 发现现有表格问答基准忽略了隐式预测类查询，构建了 779 个样本的基准来评估 LLM 在需要从历史模式推断答案时的表现。

📄 [查看论文](../entities/papers/2604-28076v1-topbench-a-benchmark-for-implicit-prediction-and-r.html)

**AEGIS** 构建了评估 AI 生成学术图像取证分析的基准，发现即使 GPT-5.1 也仅达 48.80% 整体性能，专家模型定位精度 IoU 仅 30.09%，暴露了当前检测能力的不足。

📄 [查看论文](../entities/papers/2604-28177v1-aegis-a-holistic-benchmark-for-evaluating-forensic.html)

### 领域应用

**Clinical Graph Refiner** 将 LLM 用作图结构细化器，改进 EEG 癫痫检测中的图表示学习，展示了 LLM 在医学信号处理中的跨领域应用潜力。

📄 [查看论文](../entities/papers/2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-.html)

**Data Reuse** 利用 LLM 大规模衡量学术出版中的数据重用率（43%），证明生成式 AI 可以有效监测开放科学实践的影响。

📄 [查看论文](../entities/papers/2604-28061v1-measuring-research-data-reuse-in-scholarly-publica.html)

### 智能体与仿真

**Synthetic Computers** 构建大规模合成计算机环境，利用 LLM 驱动长期生产力仿真，为评估 AI 代理在复杂真实环境中的能力提供了可扩展的测试平台。

📄 [查看论文](../entities/papers/2604-28181v1-synthetic-computers-at-scale-for-long-horizon-prod.html)

## 研究趋势

从本库论文可以看出 LLM 研究的几个关键方向：

1. **效率与扩展**：Infini-attention 探索如何让 LLM 处理更长的输入，反映了对无限上下文的追求
2. **训练鲁棒性**：PRISM 和 Exploration Hacking 分别从正反两面揭示了 LLM 训练中的分布问题——前者提出解决方案，后者发现新的失败模式
3. **评估深化**：TopBench 和 AEGIS 表明现有基准不足以评估 LLM 的真实能力，需要更细粒度、更领域特定的测试
4. **跨领域迁移**：Clinical Graph Refiner 和 Data Reuse 展示了 LLM 超越传统 NLP 任务，在医学和科学计量等领域发挥作用

## 相关论文

- [Infini-attention](../entities/papers/2404-07143-arxiv-query-searchqueryampidlist240407143ampstart0.html) — 压缩记忆实现无限上下文 Transformer
- [PRISM](../entities/papers/2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil.html) — 黑箱蒸馏解决多模态 SFT 分布漂移
- [Exploration Hacking](../entities/papers/2604-28182v1-exploration-hacking-can-llms-learn-to-resist-rl-tr.html) — LLM 学会抵抗 RL 训练
- [TopBench](../entities/papers/2604-28076v1-topbench-a-benchmark-for-implicit-prediction-and-r.html) — 表格问答隐式预测基准
- [AEGIS](../entities/papers/2604-28177v1-aegis-a-holistic-benchmark-for-evaluating-forensic.html) — AI 生成学术图像检测基准
- [Clinical Graph Refiner](../entities/papers/2604-28178v1-llm-as-clinical-graph-structure-refiner-enhancing-.html) — LLM 优化 EEG 图结构
- [Data Reuse](../entities/papers/2604-28061v1-measuring-research-data-reuse-in-scholarly-publica.html) — LLM 衡量数据重用
- [Synthetic Computers](../entities/papers/2604-28181v1-synthetic-computers-at-scale-for-long-horizon-prod.html) — LLM 驱动生产力仿真

## 相关概念

- [强化学习](reinforcement-learning.html) — LLM 后训练对齐的核心方法
- [多模态学习](multimodal-learning.html) — 扩展 LLM 到视觉等多模态输入
- [知识蒸馏](knowledge-distillation.html) — 模型压缩与知识迁移
- [基准评估](benchmarking.html) — LLM 能力的系统性评估
- [智能体](ai-agents.html) — 基于 LLM 的自主智能系统
- [AI安全与对齐](ai-safety-alignment.html) — 确保 LLM 行为安全可控
- **EMO**（[2605.06663](../entities/papers/2605-06663v1-emo-pretraining-mixture-of-experts-for-emergent-mo.html)）：提出通过文档级路由约束使 MoE 专家在语义层面涌现模块化分组，支持选择性专家使用。
- **VHG**（[2605.06660](../entities/papers/2605-06660v1-verifier-backed-hard-problem-generation-for-mathem.html)）：引入三方自博弈框架（出题者-解题者-验证器），防止奖励黑客，生成有效且困难的数学问题。
- **SimpleAudit**（[2605.06652](../entities/papers/2605-06652v1-when-no-benchmark-exists-validating-comparative-ll.html)）：正式化无基准比较安全评分，提出工具有效性链，在无真实标签时提供可复现的 LLM 安全性比较。
- **POPO**（[2605.06650](../entities/papers/2605-06650v1-beyond-negative-rollouts-positive-only-policy-opti.html)）：提出仅使用正向 rollout 的 RLVR 框架，通过概率重分配产生隐式负梯度，在 AIME 2025 上超越 GRPO。
- **StraTA**（[2605.06642](../entities/papers/2605-06642v1-strata-incentivizing-agentic-reinforcement-learnin.html)）：将显式轨迹级策略引入智能体 RL，在 ALFWorld 和 WebShop 上取得领先成功率。
- **ScaleLogic**（[2605.06638](../entities/papers/2605-06638v1-can-rl-teach-long-horizon-reasoning-to-llms-expres.html)）：揭示 RL 训练计算与推理深度间的幂律关系，证明逻辑表达能力是下游迁移的关键因素。
- **Cited but Not Verified**（[2605.06635](../entities/papers/2605-06635v1-cited-but-not-verified-parsing-and-evaluating-sour.html)）：发现 LLM 深度研究智能体的引用事实准确性仅 39-77%，更多检索反而降低准确性。
- [UniPool](../entities/papers/2605-06665v1-unipool-a-globally-shared-expert-pool-for-mixture.html) — 提出全局共享专家池替代逐层专家所有权，实现专家参数的亚线性深度缩放。
- [LongMemEval-V2](../entities/papers/2605-12493v1-longmemeval-v2-evaluating-long-term-agent-memory-t.html) — 评估长期记忆使智能体成为环境专家的基准。
- [Task-Adaptive Embedding](../entities/papers/2605-12487v1-task-adaptive-embedding-refinement-via-test-time-l.html) — LLM引导的测试时嵌入优化，改善零样本搜索与分类。
- [MEME](../entities/papers/2605-12477v1-meme-multi-entity-evolving-memory-evaluation.html) — 多实体演化记忆评估，揭示依赖推理的根本性困难。
- [Router Geometry](../entities/papers/2605-12476v1-routers-learn-the-geometry-of-their-experts-geomet.html) — 揭示SMoE中路由器与专家的几何耦合机制。
- [KV-Fold](../entities/papers/2605-12471v1-kv-fold-one-step-kv-cache-recurrence-for-long-cont.html) — 免训练的长上下文推理协议，利用KV缓存递归实现100%大海捞针检索。
- [Attractor Models](../entities/papers/2605-12466v1-solve-the-loop-attractor-models-for-language-and-r.html) — 隐式微分不动点迭代，实现可扩展的循环推理架构。
- [Multi-Stream LLMs](../entities/papers/2605-12460v1-multi-stream-llms-unblocking-language-models-with.html) — 多并行流指令微调解除聊天模型阻塞，改善效率与安全。
- [TextSeal](../entities/papers/2605-12456v1-textseal-a-localized-llm-watermark-for-provenance.html) — 无失真LLM水印，支持局部检测与蒸馏追踪。
- [AlphaGRPO](../entities/papers/2605-12495v1-alphagrpo-unlocking-self-reflective-multimodal-gen.html) — GRPO应用于统一多模态模型，解锁自反思生成能力。
- [Fast-Slow Training](../entities/papers/2605-12484v1-learning-fast-and-slow-towards-llms-that-adapt-con.html) — 快慢权重双时间尺度学习框架，提升持续适应能力。
