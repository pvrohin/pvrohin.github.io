---
name: Particle Filter
tools: [Python, NumPy, SciPy, OpenCV, SymPy, IMU, AprilTags]
image: https://opengraph.githubassets.com/1/pvrohin/Particle-Filter
description: Monte Carlo Particle Filter for 6-DOF robot pose estimation fusing IMU data with AprilTag observations, compared against EKF and VICON ground truth.
---

<div style="text-align: center;"><h1>Particle Filter</h1></div>

This project implements a **Particle Filter (Sequential Monte Carlo)** for 6-DOF robot pose estimation, developed as part of the RBE595 Robot Navigation course at **Worcester Polytechnic Institute**. It fuses **IMU inertial data** with **AprilTag visual observations** and is benchmarked against an Extended Kalman Filter (EKF) and VICON motion capture ground truth.

---

<h2 style="text-align: center;">Why Particle Filter?</h2>

The Particle Filter makes **no assumptions about the shape of the belief distribution** — unlike the EKF, which requires Gaussian noise and linearized dynamics. By representing the posterior as a set of weighted samples (particles), it can handle **multimodal distributions** and highly nonlinear motion models, at the cost of higher computational demand.

---

<h2 style="text-align: center;">Algorithm</h2>

**Initialization** — 2,000 particles are sampled from a prior distribution over robot poses (position + orientation).

**Prediction** — Each particle is propagated forward independently using IMU measurements (accelerometer + gyroscope integration), adding process noise to maintain diversity.

**Update (Weighting)** — When an AprilTag is detected, the **PnP solver** produces a pose observation. Each particle is weighted by the likelihood of observing that measurement given its state.

**Resampling** — **Low-variance resampling** is applied to focus computational resources on high-probability regions of the state space, avoiding particle degeneracy.

**Estimation** — The final pose estimate is computed as the weighted mean of all particles.

---

<h2 style="text-align: center;">Comparison: Particle Filter vs EKF</h2>

| Property | Particle Filter | Extended Kalman Filter |
|---|---|---|
| Distribution assumption | Non-parametric | Gaussian |
| Handles multimodality | Yes | No |
| Computational cost | Higher (2,000 particles) | Lower |
| Nonlinear handling | Exact (sample-based) | Approximate (Jacobian) |
| Accuracy (this project) | Comparable to EKF | Baseline |

Both methods were evaluated on 8 datasets (`studentdata0.mat` – `studentdata7.mat`) collected with a real robot equipped with an IMU and camera. RMSE metrics were computed against VICON ground truth for quantitative comparison.

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/Particle-Filter" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
