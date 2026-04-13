---
name: Extended Kalman Filter
tools: [Python, NumPy, SciPy, OpenCV, SymPy, IMU, AprilTags]
image: https://raw.githubusercontent.com/pvrohin/Extended-Kalman-Filter/master/EKF_vs_GroundTruth_vs_Observation_Model.png
description: EKF-based robot pose estimation fusing IMU accelerometer/gyroscope data with AprilTag visual landmarks, validated against VICON motion capture ground truth.
---

<div style="text-align: center;"><h1>Extended Kalman Filter</h1></div>

This project implements an **Extended Kalman Filter (EKF)** for robot state estimation by fusing data from an **Inertial Measurement Unit (IMU)** with visual pose estimates from **AprilTag landmarks**, developed as part of the RBE595 Robot Navigation course at **Worcester Polytechnic Institute**. Results are validated against VICON motion capture ground truth.

---

<h2 style="text-align: center;">Why Extended?</h2>

Unlike the standard Kalman Filter, the EKF handles **nonlinear system dynamics**. IMU-based motion propagation and camera projection are both nonlinear operations, requiring **Jacobian linearization** at each timestep. Jacobians are computed analytically using **SymPy** for symbolic differentiation.

---

<h2 style="text-align: center;">System Architecture</h2>

**State Vector** — 15 states: 3D position, 3D velocity, orientation (quaternion), and IMU biases (gyroscope + accelerometer).

**Prediction Step (IMU)** — At each IMU sample, the state is propagated forward by integrating accelerometer and gyroscope measurements. The state covariance is updated using the linearized Jacobian of the process model.

**Update Step (Vision)** — When an AprilTag observation is available, a **Perspective-n-Point (PnP)** algorithm estimates the camera pose. The residual between predicted and observed pose is used to correct the state estimate via the Kalman gain.

**Sensor Fusion** — The IMU provides high-frequency motion predictions between observations, while AprilTags supply low-frequency but accurate pose corrections, complementing each other's weaknesses.

---

<h2 style="text-align: center;">Results</h2>

<div style="text-align: center;">
  <p><strong>EKF vs Ground Truth vs Observation Model (3D Trajectory)</strong></p>
  <img src="https://raw.githubusercontent.com/pvrohin/Extended-Kalman-Filter/master/EKF_vs_GroundTruth_vs_Observation_Model.png" alt="EKF vs ground truth vs observation model" style="max-width: 700px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

<div style="text-align: center;">
  <p><strong>Position Estimation Accuracy</strong></p>
  <img src="https://raw.githubusercontent.com/pvrohin/Extended-Kalman-Filter/master/Estimated_vs_GroundTruth_Observation_Model.png" alt="Estimated vs ground truth" style="max-width: 700px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

<div style="text-align: center;">
  <p><strong>Orientation Tracking (Roll / Pitch / Yaw)</strong></p>
  <img src="https://raw.githubusercontent.com/pvrohin/Extended-Kalman-Filter/master/Orientations_Tracking_Observation_Model.png" alt="Orientation tracking" style="max-width: 700px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

The EKF trajectory closely follows the VICON ground truth, outperforming the raw observation model by smoothing sensor noise and handling measurement dropouts.

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/Extended-Kalman-Filter" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
