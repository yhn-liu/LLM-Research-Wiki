---
layout: paper
title: "An adaptive wavelet-based PINN for problems with localized high-magnitude source"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28180v1
authors: "Himanshu Pandey, Ratikanta Behera"
published: 2026-04-30
categories: cs.LG
tags: [ml]
source_url: https://arxiv.org/abs/2604.28180v1
pdf_url: https://arxiv.org/pdf/2604.28180v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: [assets/papers/2604-28180v1/fig1.png, assets/papers/2604-28180v1/fig2.png, assets/papers/2604-28180v1/fig3.png]
---

# An adaptive wavelet-based PINN for problems with localized high-magnitude source

## 基本信息

- **arXiv ID:** [2604.28180v1](https://arxiv.org/abs/2604.28180v1)
- **作者:** Himanshu Pandey, Ratikanta Behera
- **发布日期:** 2026-04-30
- **分类:** cs.LG
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2604.28180v1)

## 关键图示

<div class="paper-figure-grid">
<figure><img src="../../assets/papers/2604-28180v1/fig1.png" alt="An adaptive wavelet-based PINN Figure 1"><figcaption>Figure 1</figcaption></figure>
<figure><img src="../../assets/papers/2604-28180v1/fig2.png" alt="An adaptive wavelet-based PINN Figure 2"><figcaption>Figure 2</figcaption></figure>
<figure><img src="../../assets/papers/2604-28180v1/fig3.png" alt="An adaptive wavelet-based PINN Figure 3"><figcaption>Figure 3</figcaption></figure>
</div>

## 摘要

In recent years, physics-informed neural networks (PINNs) have gained significant attention for solving differential equations, although they suffer from two fundamental limitations, namely, spectral bias inherent in neural networks and loss imbalance arising from multiscale phenomena. This paper proposes an adaptive wavelet-based PINN (AW-PINN) to address the extreme loss imbalance characteristic of problems with localized high-magnitude source terms. Such problems frequently arise in various physical applications, such as thermal processing, electro-magnetics, impact mechanics, and fluid dynamics involving localized forcing. The proposed framework dynamically adjusts the wavelet basis function based on residual and supervised loss. This adaptive nature makes AW-PINN handle problems with high-scale features effectively without being memory-intensive. Additionally, AW-PINN does not rely on automatic differentiation to obtain derivatives involved in the loss function, which accelerates the training process. The method operates in two stages, an initial short pre-training phase with fixed bases to select physically relevant wavelet families, followed by an adaptive refinement that adapts scales and translations without populating high-resolution bases across entire domains. Theoretically, we show that under certain assumptions, AW-PINN admits a Gaussian process limit and derive its associated NTK structure. We evaluate AW-PINN on several challenging PDEs featuring localized high-magnitude source terms with extreme loss imbalances having ratios up to $10^{10}:1$. Across these PDEs, including transient heat conduction, highly localized Poisson problems, oscillatory flow equations, and Maxwell equations with a point charge source, AW-PINN consistently outperforms existing methods in its class.

## 核心贡献

- **面向局部高幅值源项的 PINN 失衡问题。** 论文聚焦一类传统 PINN 特别困难的 PDE：源项集中在很小区域或短时间内、幅值巨大，导致 PDE residual、边界/初值监督项之间初始 loss 比例可达 `10^9` 到 `10^10` 量级，优化器容易只追最大项。
- **提出 AW-PINN：自适应小波基 PINN。** 相比 W-PINN 使用固定 dyadic scales/translates 并需要预计算大规模小波矩阵，AW-PINN 先短暂预训练选择相关小波族，再把尺度和平移变成可学习参数，只在需要细尺度的位置自适应放大分辨率。
- **避免自动微分求 PDE 导数。** 方法利用小波激活函数的解析一阶/二阶导数计算残差中的微分项，类似 W-PINN，减少 autograd 负担，从而在若干实验中比 MMPINN 更快或更稳定。
- **给出理论刻画。** 作者证明在随机初始化、无限自适应小波族等假设下，AW-PINN 有零均值 Gaussian process 极限，并推导经验 NTK 可分解为线性系数贡献 `K_c` 与尺度/平移参数贡献 `K_θ`。
- **在多类强源 PDE 上验证。** 实验覆盖瞬态热传导、二维局部 Poisson、强振荡流方程和含点电荷源的 TEz Maxwell 方程，均与 W-PINN、MMPINN、baseline PINN 对比。

## 方法概述

- **阶段一：W-PINN 预训练与族选择。** 在固定小波族集合上训练短程 W-PINN；对每个小波族计算其对 PDE 残差项 `P[c_i Ψ_i]` 和边界/初值项 `B[c_i Ψ_i]` 的响应向量，并与源项/监督值做归一化内积相似度，同时保留系数绝对值最大的若干基函数。
- **阶段二：自适应小波网络。** 对选中的每个小波族 `i`，构造可学习单元 `W_i(x;θ_i)=∏_n ψ(w_{i,n} x_n + b_{i,n})`，初值来自预训练的 dyadic scale `2^j` 和 translate `-k`；最终解表示为 `û(x)=Σ_i c_i W_i(x)+B`。
- **优化与导数：** 自适应阶段用 L-BFGS 最小化普通 PINN residual + supervised loss，不引入额外 loss-balancing 权重；微分算子中的一阶/二阶导数由小波函数解析式直接计算。
- **直觉：** 固定 W-PINN 若要覆盖局部尖峰，需要全域铺设高分辨率基，内存和非凸性上升；AW-PINN 先筛出相关族，再让 `w,b` 连续移动/缩放，从而把高尺度容量集中到源项附近。

## 实验结果

- **热传导强热源：** 对 `ε=0.12/0.11/0.10`，AW-PINN 相对 L2 误差分别约 `3.52e-6/8.15e-6/8.86e-6`，均优于 W-PINN 和 MMPINN；在 `ε=0.10` 时 MMPINN 误差约 `8.46e-1` 基本失败，而 AW-PINN 仍可稳定求解，且不需要随 `ε` 降低增加 collocation 点。
- **二维 Poisson 局部源：** `ε=0.05` 时 AW-PINN 误差 `3.42e-5`，比 W-PINN `3.55e-4`、MMPINN `5.71e-4` 低约一个量级；`ε=0.02` 时 AW-PINN `2.68e-4`，仍显著优于 W-PINN `9.81e-3` 与 MMPINN `3.25e-3`。图 4.5 显示尺度参数确实向需要的位置自适应。
- **强振荡流方程：** 在 `A=100, Ts=0.05` 的时间振荡源下，AW-PINN 相对 L2 误差 `5.17e-4`，比 W-PINN `1.27e-2` 和 MMPINN `8.35e-2` 低一到两个量级。
- **TEz Maxwell 点源：** 对 `Ex/Ey/Hz` 三个场，AW-PINN 误差约 `5.31e-3/6.54e-3/9.01e-3`；W-PINN 和 MMPINN 对 `Hz` 的误差分别约 `4.52e-1` 和 `2.31e-1`，显示在三维时空、电磁点源场景下 AW-PINN 仍明显更稳。
- **训练时间：** AW-PINN 通常比 MMPINN 快得多或更可靠，但因多了自适应阶段，个别简单二维任务比 W-PINN 略慢；其优势主要体现在高尺度/强失衡问题上的准确性和稳定性。

## 局限性与注意点

- **小波族选择仍有人工成分。** 论文结论明确指出，相似度阈值、top-κ 系数选择等部分依赖手动调参，并受预训练质量影响；若预训练没有选中关键局部结构，自适应阶段可能受限。
- **小波基选择未系统展开。** 实验使用 Gaussian wavelet（一阶 Gaussian 导数），作者承认不同母小波的表现仍需系统比较。
- **泛化范围仍需扩大。** 当前覆盖若干代表性局部强源 PDE，但尚未证明对更广泛多尺度 PDE、复杂几何、高维随机/逆问题同样有效。
- **代码可用性有限。** 论文写明复现实验的代码“available on request”，不是直接公开仓库；独立复现需要额外获取实现细节和超参数。
- **理论假设与实际初始化不同。** Gaussian process/NTK 证明基于随机初始化和无限族极限，而实际模型从 W-PINN 预训练参数迁移；理论更多提供分析视角，不是对实际训练收敛的完整保证。

## 相关概念

- [物理信息神经网络](../../concepts/physics-informed-neural-networks.html)
- [科学机器学习](../../concepts/scientific-machine-learning.html)
- [神经切线核](../../concepts/neural-tangent-kernel.html)
- [小波变换](../../concepts/wavelet-transform.html)

---
*导入时间: 2026-05-02 16:44*
*来源: arXiv Daily Wiki Update 2026-05-02*
