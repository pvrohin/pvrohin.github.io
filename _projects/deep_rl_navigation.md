---
name: Goal-Driven Navigation via Deep RL
tools: [Python, PyTorch, ROS, Gazebo, TD3, LiDAR, TensorBoard]
image: https://raw.githubusercontent.com/pvrohin/Goal-Driven-Autonomous-Navigation-using-Deep-RL/master/code/training.gif
description: TD3-based deep reinforcement learning for goal-driven mobile robot navigation in Gazebo, using Velodyne LiDAR and RGB camera inputs with continuous velocity control.
---

<div style="text-align: center;"><h1>Goal-Driven Navigation via Deep Reinforcement Learning</h1></div>

This project trains a mobile robot to **autonomously navigate toward randomly placed goals while avoiding obstacles**, using the **TD3 (Twin Delayed Deep Deterministic Policy Gradient)** algorithm. The system runs in **ROS Noetic + Gazebo 11**, with a Velodyne 3D LiDAR and RGB camera as sensor inputs, outputting continuous linear and angular velocity commands.

---

<h2 style="text-align: center;">Training Demo</h2>

<div style="text-align: center;">
  <img src="https://raw.githubusercontent.com/pvrohin/Goal-Driven-Autonomous-Navigation-using-Deep-RL/master/code/training.gif" alt="Training demo" style="max-width: 700px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

---

<h2 style="text-align: center;">Simulation Environment & Sensors</h2>

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Gazebo Environment</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/Goal-Driven-Autonomous-Navigation-using-Deep-RL/master/code/env1.png" alt="Gazebo environment" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Velodyne LiDAR (RViz)</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/Goal-Driven-Autonomous-Navigation-using-Deep-RL/master/code/velodyne.png" alt="Velodyne LiDAR RViz" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h2 style="text-align: center;">Algorithm: TD3</h2>

**Twin Delayed Deep Deterministic Policy Gradient (TD3)** addresses the overestimation bias of standard actor-critic methods through three key modifications:

**1. Clipped Double Q-Learning** — Two independent critic networks estimate the Q-value; the minimum is used for the TD target, reducing overestimation.

**2. Delayed Policy Updates** — The actor and target networks update less frequently than the critics (every 2 critic updates), allowing the value estimates to stabilize before the policy changes.

**3. Target Policy Smoothing** — Noise is added to the target action during critic updates, smoothing the value function and reducing exploitation of sharp Q-function peaks.

---

<h2 style="text-align: center;">System Architecture</h2>

| Component | Details |
|---|---|
| Simulation | Gazebo 11, ROS Noetic |
| Sensors | Velodyne 3D LiDAR, RGB camera |
| Action space | Continuous linear + angular velocity |
| State space | LiDAR scan + goal direction + distance |
| RL Algorithm | TD3 (actor-critic) |
| Deep learning | PyTorch 1.10+ |
| Training monitor | TensorBoard |

The **actor network** outputs deterministic velocity commands given the current sensor state. The **dual critic networks** estimate the expected cumulative reward, providing a stable learning signal via the Bellman equation.

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/Goal-Driven-Autonomous-Navigation-using-Deep-RL" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
