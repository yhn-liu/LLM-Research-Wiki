---
layout: paper
title: "FlexiTac: A Low-Cost, Open-Source, Scalable Tactile Sensing Solution for Robotic Systems"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28156v1
authors: "Binghao Huang, Yunzhu Li"
published: 2026-04-30
categories: cs.RO, cs.AI, cs.LG
tags: [ai, ml]
source_url: https://arxiv.org/abs/2604.28156v1
pdf_url: https://arxiv.org/pdf/2604.28156v1
source_type: arxiv_daily
confidence: high
status: analyzed
key_figures: [assets/papers/2604-28156v1/fig1.png, assets/papers/2604-28156v1/fig2.png, assets/papers/2604-28156v1/fig3.png]
---

# FlexiTac: A Low-Cost, Open-Source, Scalable Tactile Sensing Solution for Robotic Systems

## 基本信息

- **arXiv ID:** [2604.28156v1](https://arxiv.org/abs/2604.28156v1)
- **作者:** Binghao Huang, Yunzhu Li
- **发布日期:** 2026-04-30
- **分类:** cs.RO, cs.AI, cs.LG
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2604.28156v1)

## 摘要

We present FlexiTac, a low-cost, open-source, and scalable piezoresistive tactile sensing solution designed for robotic end-effectors. FlexiTac is a practical "plug-in" module consisting of (i) thin, flexible tactile sensor pads that provide dense tactile signals and (ii) a compact multi-channel readout board that streams synchronized measurements for real-time control and large-scale data collection. FlexiTac pads adopt a sealed three-layer laminate stack (FPC-Velostat-FPC) with electrode patterns directly integrated into flexible printed circuits, substantially improving fabrication throughput and repeatability while maintaining mechanical compliance for deployment on both rigid and soft grippers. The readout electronics use widely available, low-cost components and stream tactile signals to a host computer at 100 Hz via serial communication. Across multiple configurations, including fingertip pads and larger tactile mats, FlexiTac can be mounted on diverse platforms without major mechanical redesign. We further show that FlexiTac supports modern tactile learning pipelines, including 3D visuo-tactile fusion for contact-aware decision making, cross-embodiment skill transfer, and real-to-sim-to-real fine-tuning with GPU-parallel tactile simulation. Our project page is available at https://flexitac.github.io/.

## 核心贡献

- **提出低成本、开源、可规模化的柔性触觉平台 FlexiTac。** 论文目标不是刷新单点传感精度，而是降低机器人学习中部署 dense tactile sensing 的门槛：传感 pad、读出板和软件接口形成“plug-in/drop-in”模块，可接入刚性夹爪、软夹爪、多指手、可穿戴采集器等多种 embodiment。
- **用 FPC–Velostat–FPC 三层密封叠层提升制造一致性。** FlexiTac V2 将电极图案直接集成到柔性印刷电路（FPC）中，替代早期手工对齐导电线的做法；Velostat 夹在上下 FPC 电极之间，外部用 laminating sheets 封装，单片制造可约 5 分钟完成。
- **设计低门槛多通道读出电子。** 读出板使用 Arduino Nano、移位寄存器和多路复用器等通用低价元件，通过 0.5 mm FFC 连接，100 Hz 串口输出同步 tactile stream；同一板可兼容不同分辨率 pad，降低复制和扩展难度。
- **明确成本与规模化路径。** 完整单元约 30 美元，其中 Arduino 约 25 美元；FPC 与 PCB 在 1000 件量级成本可降到每对 FPC 1.36 美元、每块读出 PCB 2.61 美元。作者也指出可通过把 MCU 集成进 PCB 进一步降本，但当前保留 Arduino 是为了易组装、调试和复现。
- **展示 FlexiTac 支持现代触觉学习管线。** 论文用 3D 视触觉融合、跨 embodiment 技能迁移、real-to-sim-to-real tactile simulation 三条路径说明该硬件不仅能采数据，还能接入 diffusion policy、VLA/触觉表示学习、GPU 并行触觉仿真和 RL fine-tuning。

## 方法概述

FlexiTac pad 基于压阻式矩阵：上下两层 FPC 的正交电极形成 taxel 网格，机械压力改变 Velostat 电阻，读出电路将其转成电压信号。典型 pad 厚度小于 1 mm，V2 pitch 为 2 mm，可制成 12×32、8×16、16×16、32×32 tactile mat 等多种形态。FPC 电极之间加入窄槽，一方面增加柔顺性以贴合曲面或软表面，另一方面把局部变形集中到压阻膜上以提升灵敏度；底层较长走线处用 supporting beam 和 0.2 mm polyimide stiffener 增强结构可靠性。

读出板设计强调可复现和低接线复杂度。以 32×16 board 为例，系统用一个 16-channel multiplexer 做模拟信号路由，用四个 8-bit shift register 做数字寻址，从而用较少 GPIO 扫描高维矩阵。数据以 100 Hz 通过串口发往主机，方便与视觉、proprioception、控制频率对齐。

在系统集成上，论文首先描述 3D-ViTac 式融合：多视角 RGB-D 重建为 3D visual point cloud；每个 taxel 通过标定后的 pad-to-gripper transform 和机器人正运动学提升到 3D tactile point，并附带接触强度特征；视觉点与触觉点合并成带 modality indicator 的统一 3D 点集，供 point-cloud backbone/diffusion policy 做闭环控制。

跨 embodiment 场景中，FlexiTac 同时装在便携式人类数据采集器和 xArm 机器人夹爪上，保持一致触觉格式，帮助把人类自然操作中的压力调节、抓稳和微调技能迁移到机器人。仿真场景中，FlexiTac 被建模为一组按真实 taxel 布局分布的接触点，在 GPU 并行 simulator 中用 SDF 查询 penetration depth 和 normal velocity，并用 Kelvin–Voigt penalty model 生成 normal force/penetration 信号；校准只调 normal stiffness 和 damping，并对真实/仿真信号用一致归一化。

## 实验结果

这篇论文更像硬件平台与系统展示，而非以单一 benchmark 指标为中心的实验论文。硬件层面的关键结果包括：传感 pad 可快速制造（约 5 分钟/片），薄而柔顺，可安装到 Robotiq、xArm、ALOHA、LeRobot、软 fin gripper、Franka tactile skin、tactile glove、Dexmate 等不同平台；读出板可在 100 Hz 输出同步矩阵信号；整套系统在小批量下保持约 30 美元级别成本，并具备量产降本空间。

系统能力展示包括三类。第一，3D 视触觉融合中，FlexiTac 的 taxel 能被几何提升为 3D tactile points，与 RGB-D 点云统一表示，从而让策略在视觉遮挡或接触调节任务中显式利用接触分布。第二，跨 embodiment 数据采集中，同一 tactile interface 同时服务人类便携采集器与 xArm 平台，使触觉观测格式在不同形态之间保持一致，便于学习从人类示范到机器人执行的接触依赖技能。第三，real-to-sim-to-real 管线中，矩阵压阻信号比高维 optical tactile image 更容易仿真，作者用 taxel-level contact point、Kelvin–Voigt normal force 和简单校准实现真实/仿真 tactile histogram 对齐，支持大规模仿真 RL fine-tuning。

从论文证据看，FlexiTac 的价值主要在“可部署性 + 可规模化数据接口”：它牺牲了部分触觉模态丰富性（例如不直接测振动、温度、精细纹理或剪切力），换取低成本、薄型、可定制、易安装和仿真友好的压力分布。对于机器人学习研究，这种取舍比追求单个传感器的最高分辨率更实用。

## 局限性与注意点

- 论文开头明确承认当前机器人触觉远弱于生物皮肤，FlexiTac 主要测压力/法向接触分布，不覆盖振动、温度、纹理等丰富触觉，也在仿真中有意省略 shear force 以降低复杂度。
- 论文没有给出长期耐久性、漂移、重复加载迟滞、温湿度影响、绝对力标定误差等系统量化指标；部署到高负载或高磨损任务前仍需工程验证。
- 100 Hz 对许多 manipulation 任务足够，但对高速滑移检测、冲击或振动触觉可能不足。
- real-to-sim-to-real 管线依赖简单 normal-force 模型和少量参数校准，适合结构化压力模式，但未必能覆盖复杂摩擦、切向剪切和材料非线性。


## 相关概念

- [多模态学习](../../concepts/multimodal-learning.html)
- [强化学习](../../concepts/reinforcement-learning.html)
- [基准评估](../../concepts/benchmarking.html)
- [医学AI](../../concepts/medical-ai.html)

---
*导入时间: 2026-05-02 16:44*
*来源: arXiv Daily Wiki Update 2026-05-02*
