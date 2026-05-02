---
layout: paper
title: "OmniRobotHome: A Multi-Camera Platform for Real-Time Multiadic Human-Robot Interaction"
created: 2026-05-02
updated: 2026-05-02
type: paper
arxiv_id: 2604.28197v1
authors: "Junyoung Lee, Sookwan Han, Jeonghwan Kim"
published: 2026-04-30
categories: cs.RO, cs.CV
tags: [cv]
source_url: https://arxiv.org/abs/2604.28197v1
pdf_url: https://arxiv.org/pdf/2604.28197v1
source_type: arxiv_daily
confidence: high
status: analyzed
---

# OmniRobotHome: A Multi-Camera Platform for Real-Time Multiadic Human-Robot Interaction

## 基本信息

- **arXiv ID:** [2604.28197v1](https://arxiv.org/abs/2604.28197v1)
- **作者:** Junyoung Lee, Sookwan Han, Jeonghwan Kim et al.
- **发布日期:** 2026-04-30
- **分类:** cs.RO, cs.CV
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2604.28197v1)

## 关键图示

<div class="paper-figure-grid">
<figure><img src="../../assets/papers/2604-28197v1/fig1.png" alt="OmniRobotHome: A Multi-Camera Platform for Real-Time Multiadic Human-Robot Interaction Figure 1"><figcaption>Figure 1</figcaption></figure>
<figure><img src="../../assets/papers/2604-28197v1/fig2.png" alt="OmniRobotHome: A Multi-Camera Platform for Real-Time Multiadic Human-Robot Interaction Figure 2"><figcaption>Figure 2</figcaption></figure>
<figure><img src="../../assets/papers/2604-28197v1/fig3.png" alt="OmniRobotHome: A Multi-Camera Platform for Real-Time Multiadic Human-Robot Interaction Figure 3"><figcaption>Figure 3</figcaption></figure>
</div>

## 摘要

Human-robot collaboration has been studied primarily in dyadic or sequential settings. However, real homes require multiadic collaboration, where multiple humans and robots share a workspace, acting concurrently on interleaved subtasks with tight spatial and temporal coupling. This regime remains underexplored because close-proximity interaction between humans, robots, and objects creates persistent occlusion and rapid state changes, making reliable real-time 3D tracking the central bottleneck. No existing platform provides the real-time, occlusion-robust, room-scale perception needed to make this regime experimentally tractable. We present OmniRobotHome, the first room-scale residential platform that unifies wide-area real-time 3D human and object perception with coordinated multi-robot actuation in a shared world frame. The system instruments a natural home environment with 48 hardware-synchronized RGB cameras for markerless, occlusion-robust tracking of multiple humans and objects, temporally aligned with two Franka arms that act on live scene state. Continuous capture within this consistent frame further supports long-horizon human behavior modeling from accumulated trajectories. The platform makes the multiadic collaboration regime experimentally tractable. We focus on two central problems: safety in shared human-robot environments and human-anticipatory robotic assistance, and show that real-time perception and accumulated behavior memory each yield measurable gains in both.

## 核心贡献

- 提出 **OmniRobotHome**：一个 23.1 m² 住宅尺度物理 AI 测试床，把 48 个硬件同步 RGB 摄像头、12 个边缘节点、统一世界坐标系和两台 Franka Research 3 机械臂集成到同一闭环系统中。
- 将问题从常见的双人/顺序式人机协作推进到 **multiadic collaboration**：多个人、多个机器人和多个对象在同一空间中并发行动、任务相互依赖、存在密集遮挡与快速状态变化。
- 提供端到端实时感知管线：多视角人体检测与 2D 姿态估计、RANSAC 三角化 3D 全身关键点、基于学习的 RGB stereo 6D 物体跟踪，并与机器人控制流时间对齐。
- 证明持续无标记捕获形成的 **human behavior memory** 不只是数据记录，而能直接提升安全策略和预期式辅助：早期轨迹记忆可减少碰撞，部分演示可帮助推断物体放置意图。
- 通过安全共存、意图感知放置、意图感知递送和系统消融，展示房间尺度实时 3D 状态是让 multiadic HRI 变得可观测、可操作和可实验评估的核心基础设施。

## 方法概述

- **硬件与同步：** 系统覆盖 23.1 m² 居家空间，48 个 RGB 摄像头以 30 Hz 硬件同步；两台 Franka 机械臂通过时间戳与感知输出对齐。两个摄像头构成立体对用于桌面物体 6D 位姿跟踪。
- **标定：** 每个相机用 ChArUco 做内参标定；外参通过 16 个分布式 ChArUco 板、PnP、二分图位姿图和 bundle adjustment 统一到单一世界坐标系；机器人基座再通过 hand-eye calibration 注册到该坐标系。
- **人体实时 3D 感知：** 48 路原始数据约 13.5 GB/s，因此在 12 个边缘节点上并行运行 TensorRT 优化的 YOLO 检测与 RTMPose 2D whole-body keypoint；中心服务器只接收关键点和置信度，使用 RANSAC 多视角三角化和 One Euro Filter 输出稳定 3D 姿态。
- **物体 6D 跟踪：** 因为深度相机难以满足多路硬件同步，论文使用 RGB stereo：FoundationStereo 估计 metric depth，YOLO-E 分割，FoundationPose 从模板 mesh 做无标记 6D tracking；无 CAD 的物体用密集相机阵列和 MV-SAM3D 离线重建 mesh。
- **任务设计：** 核心实验是厨房整理：两台机械臂把 12 个物品分类送至水槽或架子，人可自由移动。安全策略比较无感知、静态半径、动态速度自适应安全区，以及加入历史接近方向记忆的 Behavior Learning；意图预测则把部分人类放置演示转成文本，比较 lookup、LLM、LLM+reasoning。

## 实验结果

- **安全共存：** Non-aware 最快但平均 387.5 次 human hits；静态 0.5m 半径降至 73.5 次但周期 89.33s；静态 2.0m 几乎无碰撞但周期暴涨至 432.53s。Dynamic 策略把碰撞降至 28.5 次且周期 63.12s；加入 Behavior Learning 后进一步降至 21.5 次，周期几乎不变（62.81s）。
- **意图感知放置：** 在 12 个物体中只观察 25% 演示时，Lookup 为 62.5%，LLM 为 88.9%；观察 50% 后 LLM 和 LLM+Reasoning 均达到 100%，而 Lookup 需完整历史才到 100%。
- **行为记忆曲线：** 安全任务中少量早期轨迹已能捕捉主要接近模式并显著降低碰撞；周期时间变化低于 1%。意图预测则要求演示覆盖两个类别后才稳定，低演示数下 LLM 可能把单个观察模式错误泛化。
- **定性意图递送：** 系统能根据 3D 姿态与场景上下文推断“浇水壶、芥末、饮料”等目标物，并根据实时手部关键点在线更新 handover 轨迹。
- **系统消融：** 自定义标定平均重投影误差 1.21 px，优于 COLMAP 的 1.42 px；48 摄像头下超过 80% 房间体素被至少 4 个视角覆盖，40 个以上摄像头时关节不可观测情况近乎消失，35 个以上时三角化误差界趋于稳定。

## 局限性与注意点

- 评估发生在单个布置好的房间、两台固定基座机械臂和任务特定控制器上；跨户型、跨机器人形态、移动机器人和通用控制接口的泛化仍未解决。
- 系统需要大量固定相机、边缘计算节点和精细标定，工程部署成本较高；论文也提示 30–35 个摄像头可提供一定准确性，但会留下空间死角。
- 实验中的安全策略和意图任务相对结构化，不能直接等同于开放家庭环境下的任意任务规划与安全保证。
- 使用 LLM/VLM 做意图推断时存在低样本误泛化问题；论文中的 k=1、k=3 示例显示推理链有时会过度依赖少量演示并抑制模型原有类别先验。
- 后续价值很大程度取决于数据公开与标注质量，包括同步多方序列、3D 轨迹、物体位姿、机器人状态和任务注释是否足够完整。

## 相关概念

- [机器人学习](../../concepts/robot-learning.html)
- [人机协作](../../concepts/human-robot-interaction.html)
- [多智能体系统](../../concepts/multi-agent-systems.html)
- [三维感知](../../concepts/3d-perception.html)
- [视觉语言模型](../../concepts/vision-language-models.html)

---
*导入时间: 2026-05-02 06:01*
*来源: arXiv Daily Digest 2026-05-02*
