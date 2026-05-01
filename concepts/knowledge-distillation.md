---
layout: concept
title: 知识蒸馏
created: 2026-05-01
updated: 2026-05-01
type: concept
tags: [distillation, teacher-student, model-compression, black-box, policy-distillation]
papers:
  - 2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil
---

# 知识蒸馏

## 定义

知识蒸馏（Knowledge Distillation）是一种模型压缩技术，通过将大型教师模型（teacher model）的知识迁移到小型学生模型（student model）中，使学生模型在保持较小规模的同时获得接近教师模型的性能。其核心思想是利用教师模型的软标签（soft labels）或中间表示来指导学生模型的学习，而不仅仅是使用硬标签（hard labels）。在大语言模型时代，知识蒸馏已成为模型部署和能力迁移的关键技术。

## 关键文献与发现

### PRISM: 黑箱在线策略蒸馏的预对齐方法

> Wang et al. (2026). *PRISM: Pre-alignment via Black-box On-policy Distillation for Multimodal Reinforcement Learning.* arXiv:2604.28123v1

PRISM 揭示了标准 LMM 训练流程（SFT→RLVR）中的一个关键问题：监督微调（SFT）会引入分布漂移（distribution drift），导致模型既不能保留预训练能力，也无法忠实匹配监督分布。在多模态推理场景中，这一问题被进一步放大——感知错误和推理失败遵循不同的漂移模式，并在后续 RL 阶段复合。

**方法**：PRISM 提出三阶段训练管道（SFT→对齐→RLVR），在 SFT 和 RLVR 之间插入显式分布对齐阶段。对齐阶段基于在线策略蒸馏（OPD）原理，将策略与一个 MoE 判别器之间的交互建模为黑盒响应级对抗博弈。判别器包含专门的感知专家和推理专家，从不同维度提供解耦的纠正信号。该方法无需访问教师模型的 logits，仅需响应级别的交互即可工作。为此，作者从 Gemini 3 Flash 策划了 11.3 万条高保真演示。

**发现**：在 Qwen3-VL 上，PRISM 在 GRPO、DAPO、GSPO 等多种 RL 算法和多模态基准测试中持续改进了下游 RLVR 性能，验证了分布对齐阶段对减轻 SFT 漂移的有效性。

### 知识蒸馏的文献脉络

PRISM 的工作建立在知识蒸馏领域的长期研究基础上：

- **基础理论（2006–2015）**：Caruana 等人（2006）首次提出模型压缩概念；Hinton 等人（2014）正式定义了温度缩放的软标签和蒸馏损失函数；FitNets（2015）提出通过中间层表示进行更深的蒸馏。
- **白箱蒸馏（2016–2020）**：Attention Transfer（2016）迁移注意力分布；TinyBERT（2019）等探索了 Transformer 架构的专项蒸馏方法。
- **黑箱蒸馏兴起（2020–2024）**：ChatGPT 发布后，通过 API 输出进行知识蒸馏成为热潮。Alpaca、Vicuna 等开源模型展示了黑箱蒸馏在 LLM 中的实践效果。
- **在线策略蒸馏（2024–2026）**：PRISM 等工作进一步提出黑箱在线策略蒸馏（Black-box OPD），解决了离线蒸馏中分布偏移的根本问题。

## 技术图景

### 蒸馏范式

- **白箱蒸馏**：访问教师模型的完整权重和中间表示，进行深层知识迁移
- **黑箱蒸馏**：仅通过教师模型的 API 输出（概率分布或文本）进行蒸馏（PRISM 采用此范式）
- **在线蒸馏**：教师和学生同时训练，动态更新知识（PRISM 的 OPD 属于此类）
- **离线蒸馏**：先训练教师模型，再用其输出训练学生模型

### 蒸馏目标

- **logit 蒸馏**：匹配教师和学生模型的输出概率分布
- **特征蒸馏**：对齐中间层的特征表示
- **关系蒸馏**：保持样本间关系结构的一致性
- **策略蒸馏**：在强化学习中迁移教师的决策策略（PRISM 的核心关注）

### 在线策略蒸馏（OPD）

PRISM 提出的黑箱 OPD 是当前蒸馏技术的前沿方向：
- 学生模型在自身策略分布上采样，并从教师模型获取反馈
- 避免离线蒸馏中的分布偏移（distribution shift）
- 无需访问教师权重，仅需响应级别的交互

## 研究前沿

基于 PRISM 及现有文献，以下问题仍待解决：

1. **蒸馏税**：学生模型在蒸馏后可能出现能力退化，如何最小化性能损失仍是核心挑战
2. **分布偏移**：PRISM 虽缓解了离线蒸馏中的分布偏移，但在线蒸馏的理论保证仍不完善
3. **可扩展性**：对于超大模型，完全蒸馏所有知识的计算成本依然很高
4. **评估标准**：如何全面评估蒸馏后模型的能力保持程度仍缺乏统一标准
5. **安全性**：蒸馏可能转移教师模型的安全对齐问题，如何保证蒸馏后的安全性
6. **法律与伦理**：通过 API 输出蒸馏商业模型可能涉及知识产权问题
7. **多任务蒸馏**：同时从多个教师模型蒸馏不同能力的挑战

## 相关论文

- [PRISM: Pre-alignment via Black-box On-policy Distillation for Multimodal Reinforcement Learning](../entities/papers/2604-28123v1-prism-pre-alignment-via-black-box-on-policy-distil.html) — 提出黑箱在线策略蒸馏（Black-box OPD），在多模态强化学习中实现无需访问权重的高效知识迁移和预对齐

## 相关概念

- [大语言模型](large-language-model.html) — 知识蒸馏的主要应用对象
- [强化学习](reinforcement-learning.html) — 策略蒸馏是强化学习中的重要技术
- [多模态学习](multimodal-learning.html) — 多模态场景下的蒸馏应用
- [AI安全与对齐](ai-safety-alignment.html) — 蒸馏过程中的安全对齐问题
