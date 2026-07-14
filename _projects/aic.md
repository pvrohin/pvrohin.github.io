---
name: Intrinsic AI for Industry Challenge - Robot Learning Pipeline
tools: [Python, ROS 2, Gazebo, LeRobot, ACT, Docker]
image: /assets/AIC/AIC.png
description: Robot learning pipeline for precision cable-insertion manipulation, built for the Intrinsic AI for Industry Challenge.
---

<div style="text-align: center;"><h1>Intrinsic AI for Industry Challenge - Robot Learning Pipeline</h1></div>

---

![AIC](/assets/AIC/AIC_web.gif)

---

This project was built for the **Intrinsic AI for Industry Challenge**, an open competition for developers and roboticists tackling high-impact problems in robotics and manufacturing. Our team trained a robot to autonomously insert cable connectors (SFP and SC plugs) into randomized ports on a task board, a task demanding **sub-millimeter precision**, **contact-aware behavior**, and **generalization across varied environments**. The stack combined **ROS 2**, **Gazebo simulation**, and a custom **LeRobot**-based data collection and training pipeline.

**Code:** [aic — data_collection_pipeline_package](https://github.com/shruthibalaji2307/aic/tree/rohin/data_collection_pipeline_package)

---

<h2 style="text-align: center;">Task Overview</h2>

The challenge required an autonomous policy to insert cable connectors into randomized ports on a task board in simulation, evaluated via an organizer-provided orchestration engine that handled simulation launching, robot control, and sensor fusion. Our submission was a containerized **ROS 2** node implementing the cable-insertion policy, following the `aic_model` framework's templated lifecycle-node structure.

---

<h2 style="text-align: center;">Data Collection Pipeline</h2>

We built a **custom LeRobot integration** incorporating ROS 2 control, multi-camera observations, and a 26-dimensional robot state directly into the training and data collection pipeline.

To avoid the noise of manual teleoperation, we developed a **passive observer pipeline** that recorded ground-truth CheatCode actions as demonstrations, producing consistent, low-noise supervision at scale. Actions were encoded using an **SE(3) relative pose representation** (relative deltas rather than absolute targets), which improved robustness to randomized board positions.

The resulting dataset spanned **hundreds of demonstrations and approximately 363,000 frames**, with automated tooling for curation.

---

<h2 style="text-align: center;">Policy Training</h2>

Using the collected dataset, we trained **Action Chunking Transformer (ACT)** policies with multi-view camera observations and robot state as input for sequential manipulation.

---

<h2 style="text-align: center;">Lessons Learned</h2>

1. **Simulation Fidelity** — physics quality and rollout throughput directly affect learning outcomes.
2. **Data Quality Over Quantity** — consistent demonstrations proved more valuable than additional episodes.
3. **Diversity Over Repetition** — interleaving diverse environments improved generalization significantly.


