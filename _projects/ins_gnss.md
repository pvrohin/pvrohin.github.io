---
name: INS/GNSS Integration with UKF
tools: [Python, NumPy, SciPy, Matplotlib, Pandas, UKF, GPS]
image: https://opengraph.githubassets.com/1/pvrohin/INSS-GNSS-Integration
description: INS and GNSS sensor fusion using the Unscented Kalman Filter with WGS84 Earth model — implemented in both feedforward and feedback architectures for robust navigation.
---

<div style="text-align: center;"><h1>INS/GNSS Integration with Unscented Kalman Filter</h1></div>

This project implements **Inertial Navigation System (INS) and Global Navigation Satellite System (GNSS) integration** using the **Unscented Kalman Filter (UKF)**, developed as part of the RBE595 Robot Navigation course at **Worcester Polytechnic Institute**. Two complementary filter architectures are implemented and compared.

---

<h2 style="text-align: center;">Why UKF?</h2>

The navigation equations for INS/GNSS fusion are highly nonlinear — involving rotation matrices, Earth curvature corrections, and gravity models. The **EKF** approximates these with Jacobians, which can introduce significant linearization errors. The **UKF** instead uses **sigma points** (the Unscented Transform) to propagate the distribution through the true nonlinear function, achieving higher accuracy without requiring analytic derivatives.

---

<h2 style="text-align: center;">Two Architectures</h2>

**Feedforward Architecture (12-state)**

The INS propagates the full navigation solution independently. GNSS measurements are fused by the UKF to directly correct the current position, velocity, and orientation estimates. The state vector contains:
- 3D position (latitude, longitude, altitude)
- 3D velocity (North/East/Down)
- Orientation (roll, pitch, yaw)

**Feedback Architecture (15-state)**

Extends the feedforward design with **3 additional IMU bias states** (gyroscope and accelerometer). The UKF estimates sensor biases alongside the navigation state, and the corrections are **fed back** into the INS mechanization loop to continuously compensate for drift — achieving better long-term accuracy.

---

<h2 style="text-align: center;">Earth & Gravity Models</h2>

Navigation accuracy depends on precise modeling of the Earth's geometry and gravity field:

- **WGS84 ellipsoidal Earth model** — captures the oblate shape of the Earth for accurate latitude/longitude/altitude conversion
- **Somigliana gravity model** — computes surface gravity as a function of latitude, with vertical corrections for altitude
- **Earth rotation compensation** — angular velocity of the Earth is subtracted from gyroscope measurements to isolate true body rotation

---

<h2 style="text-align: center;">UKF Sigma Point Generation</h2>

The Julier symmetric sigma point scheme is used. For an n-dimensional state, 2n+1 sigma points are generated:

$$\mathcal{X}_0 = \hat{x}, \quad \mathcal{X}_i = \hat{x} \pm \sqrt{(n+\lambda)P_i}$$

These are propagated through the nonlinear process model, and the mean and covariance are recovered via weighted summation — capturing higher-order moments of the distribution.

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/INSS-GNSS-Integration" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
