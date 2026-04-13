---
name: AutoCalib - Camera Calibration
tools: [Python, OpenCV, NumPy, SciPy, Zhang's Method, SVD]
image: https://raw.githubusercontent.com/pvrohin/AutoCalib/master/Results/Reprojected_0.jpg
description: Camera intrinsic calibration from scratch using Zhang's method, SVD-based homography estimation, and Levenberg-Marquardt optimization with radial distortion modeling.
---

<div style="text-align: center;"><h1>AutoCalib: Camera Calibration from Scratch</h1></div>

**AutoCalib** is a complete implementation of **camera intrinsic calibration** built entirely from first principles using NumPy, OpenCV, and SciPy — without relying on OpenCV's built-in calibration functions. The system recovers the camera intrinsic matrix and distortion coefficients from checkerboard images using **Zhang's calibration method**.

---

<h2 style="text-align: center;">Calibration Pipeline</h2>

**1. Corner Detection** — Checkerboard corners are detected in 13 calibration images using `cv2.findChessboardCorners` with sub-pixel refinement via `cv2.cornerSubPix`.

**2. Homography Estimation** — For each image, a homography between the checkerboard world plane and the image plane is computed from scratch using **SVD (Singular Value Decomposition)**.

**3. Intrinsic Matrix Estimation** — Zhang's method constructs a system of equations from the homographies, solved via SVD to recover the 5-parameter intrinsic matrix **K** (focal lengths, principal point, skew).

**4. Extrinsic Recovery** — Rotation and translation matrices are extracted from each homography using the calibrated **K**.

**5. Non-Linear Optimization** — All parameters (intrinsics + extrinsics + radial distortion coefficients k₁, k₂) are refined jointly using **Levenberg-Marquardt** via `scipy.optimize.least_squares`, minimizing reprojection error.

---

<h2 style="text-align: center;">Reprojection Results</h2>

Red circles show the reprojected checkerboard corners overlaid on undistorted calibration images, validating the accuracy of the recovered camera parameters.

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoCalib/master/Results/Reprojected_0.jpg" alt="Reprojected 0" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoCalib/master/Results/Reprojected_1.jpg" alt="Reprojected 1" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>
<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoCalib/master/Results/Reprojected_4.jpg" alt="Reprojected 4" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoCalib/master/Results/Reprojected_5.jpg" alt="Reprojected 5" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>
<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoCalib/master/Results/Reprojected_8.jpg" alt="Reprojected 8" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoCalib/master/Results/Reprojected_11.jpg" alt="Reprojected 11" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/AutoCalib" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
