---
name: Structure from Motion
tools: [Python, OpenCV, NumPy, SciPy, RANSAC, Bundle Adjustment]
image: https://raw.githubusercontent.com/pvrohin/Structure-from-Motion-/master/Phase%201/P3Data/Results/BA_with_camera_pose.png
description: Incremental SfM pipeline reconstructing 3D point clouds and camera poses from 2D images using feature matching, triangulation, PnP, and bundle adjustment.
---

<div style="text-align: center;"><h1>Structure from Motion</h1></div>

This project implements a complete **incremental Structure-from-Motion (SfM)** pipeline that simultaneously reconstructs the **3D structure of a scene** and estimates the **camera pose** for each image, using only a set of 2D photographs as input. It was developed as part of the RBE549 Computer Vision course at **Worcester Polytechnic Institute**.

---

<h2 style="text-align: center;">Pipeline</h2>

**1. Feature Matching** — SIFT features are extracted and matched across image pairs. Matches are filtered first by homography constraints, then by RANSAC to remove outliers.

**2. Fundamental Matrix Estimation** — The fundamental matrix **F** is computed using the 8-point algorithm with Hartley normalization and RANSAC-based outlier rejection.

**3. Essential Matrix & Camera Pose** — The essential matrix **E** is recovered from **F** and the known camera intrinsics. Four candidate poses are extracted via SVD, and the correct one is selected using **cheirality checks** (all reconstructed points must be in front of both cameras).

**4. Linear Triangulation** — 3D world coordinates for matched feature pairs are recovered using the **Direct Linear Transform (DLT)**, establishing the initial point cloud.

**5. Non-Linear Triangulation** — Triangulated points are refined by minimizing reprojection error using Levenberg-Marquardt optimization.

**6. Perspective-n-Point (PnP)** — New cameras are registered using **Linear PnP** (DLT-based) followed by **Non-Linear PnP** refinement. RANSAC is applied to handle outlier correspondences.

**7. Bundle Adjustment** — All camera poses and 3D points are jointly refined using sparse **bundle adjustment** to minimize total reprojection error across all views.

---

<h2 style="text-align: center;">3D Reconstruction Results</h2>

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Initial Triangulation</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/Structure-from-Motion-/master/Phase%201/P3Data/Results/1_2/possible_world_coords.png" alt="Possible world coordinates" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>After Cheirality Check</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/Structure-from-Motion-/master/Phase%201/P3Data/Results/1_2/corrected_world_coords.png" alt="Corrected world coordinates" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>
<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>After Non-Linear Refinement</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/Structure-from-Motion-/master/Phase%201/P3Data/Results/1_2/refined_world_coords.png" alt="Refined world coordinates" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>With Camera Pose (Image Pair 1-2)</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/Structure-from-Motion-/master/Phase%201/P3Data/Results/1_2/with_camera_pose.png" alt="With camera pose 1-2" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h2 style="text-align: center;">Bundle Adjustment</h2>

<div class="row">
  <div class="col-md-4" style="text-align: center;">
    <p><strong>Before Bundle Adjustment</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/Structure-from-Motion-/master/Phase%201/P3Data/Results/before_BA.png" alt="Before bundle adjustment" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-4" style="text-align: center;">
    <p><strong>After Bundle Adjustment</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/Structure-from-Motion-/master/Phase%201/P3Data/Results/BA.png" alt="After bundle adjustment" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-4" style="text-align: center;">
    <p><strong>Final Point Cloud with Camera Poses</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/Structure-from-Motion-/master/Phase%201/P3Data/Results/BA_with_camera_pose.png" alt="Bundle adjustment with camera pose" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/Structure-from-Motion-" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
