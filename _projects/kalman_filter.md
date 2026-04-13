---
name: Kalman Filter
tools: [Python, NumPy, Matplotlib]
image: https://raw.githubusercontent.com/pvrohin/Kalman-Filter/master/Result.png
description: 6-state Kalman Filter for 3D position and velocity tracking of a lightweight object, evaluated across low-noise, high-noise, and velocity-measurement scenarios.
---

<div style="text-align: center;"><h1>Kalman Filter</h1></div>

This project implements a **linear Kalman Filter** for estimating the 3D position and velocity of a 27-gram object using noisy sensor measurements, developed as part of the RBE595 Robot Navigation course at **Worcester Polytechnic Institute**. The filter is evaluated across multiple data scenarios and compared against motion capture ground truth.

---

<h2 style="text-align: center;">State Space</h2>

The filter tracks a **6-dimensional state vector** — three spatial coordinates and their corresponding velocities:

$$\mathbf{x} = [x, y, z, \dot{x}, \dot{y}, \dot{z}]^\top$$

The system evolves according to the linear state-space model:

$$\mathbf{x}_{k+1} = A\mathbf{x}_k + B\mathbf{u}_k + \mathbf{w}_k$$
$$\mathbf{z}_k = H\mathbf{x}_k + \mathbf{v}_k$$

where \\(\mathbf{w}_k \sim \mathcal{N}(0, Q)\\) is process noise and \\(\mathbf{v}_k \sim \mathcal{N}(0, R)\\) is measurement noise.

---

<h2 style="text-align: center;">Filter Steps</h2>

**Prediction:**
$$\hat{\mathbf{x}}_{k|k-1} = A\hat{\mathbf{x}}_{k-1|k-1}$$
$$P_{k|k-1} = AP_{k-1|k-1}A^\top + Q$$

**Update:**
$$K_k = P_{k|k-1}H^\top(HP_{k|k-1}H^\top + R)^{-1}$$
$$\hat{\mathbf{x}}_{k|k} = \hat{\mathbf{x}}_{k|k-1} + K_k(\mathbf{z}_k - H\hat{\mathbf{x}}_{k|k-1})$$
$$P_{k|k} = (I - K_kH)P_{k|k-1}$$

---

<h2 style="text-align: center;">Results</h2>

The plot below compares the Kalman-filtered trajectory against ground truth motion capture data across three scenarios: low noise, high noise, and velocity measurements.

<div style="text-align: center;">
  <img src="https://raw.githubusercontent.com/pvrohin/Kalman-Filter/master/Result.png" alt="Kalman filter 3D trajectory result" style="max-width: 700px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

The filter successfully suppresses noise in all scenarios, closely tracking the true trajectory even under high measurement uncertainty.

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/Kalman-Filter" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
