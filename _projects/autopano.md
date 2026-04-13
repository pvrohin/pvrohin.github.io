---
name: AutoPano - Image Stitching
tools: [Python, OpenCV, NumPy, scikit-image, SciPy, Deep Learning]
image: https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/pano_image_1.png
description: Automated image stitching pipeline combining classical computer vision and deep learning to generate seamless panoramas from overlapping images.
---

<div style="text-align: center;"><h1>AutoPano: Image Stitching</h1></div>

**AutoPano** is an automated panoramic image stitching system developed as part of a geometric computer vision course at **Worcester Polytechnic Institute**. The system merges multiple overlapping photographs into seamless wide-angle composites through two implementations: a **classical computer vision pipeline** (Phase 1) and a **deep learning-based approach** (Phase 2).

---

<h2 style="text-align: center;">Phase 1: Classical Pipeline</h2>

The classical pipeline processes image pairs through six sequential stages, from raw input to stitched panorama.

---

<h3 style="text-align: center;">Step 1: Corner Detection</h3>

Salient keypoints are identified using the **Harris** and **Shi-Tomasi** corner detection algorithms, locating geometrically distinctive regions across each image.

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/corner_images_0.png" alt="Corner detection image 0" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/corner_images_1.png" alt="Corner detection image 1" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>
<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/corner_images_2.png" alt="Corner detection image 2" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/corner_images_3.png" alt="Corner detection image 3" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h3 style="text-align: center;">Step 2: Adaptive Non-Maximal Suppression (ANMS)</h3>

Raw corner responses are filtered using **ANMS** to retain only the most distinctive corners while enforcing even spatial distribution — preventing feature clustering near high-gradient regions.

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/anms_images_0.png" alt="ANMS image 0" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/anms_images_1.png" alt="ANMS image 1" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>
<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/anms_images_2.png" alt="ANMS image 2" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/anms_images_3.png" alt="ANMS image 3" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h3 style="text-align: center;">Step 3: Feature Descriptor Extraction</h3>

An **8×8 patch-based descriptor** is extracted around each retained corner. Patches are Gaussian-smoothed and normalized to produce robust, comparison-ready feature vectors.

<div style="text-align: center;">
  <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/feature_descriptor_image.png" alt="Feature descriptor" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

---

<h3 style="text-align: center;">Step 4: Feature Matching</h3>

Correspondences between image pairs are established via **ratio-test validation**, filtering ambiguous matches by comparing distances to the best and second-best candidate descriptors.

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/feature_matched_image_0.png" alt="Feature matches 0" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/feature_matched_image_1.png" alt="Feature matches 1" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h3 style="text-align: center;">Step 5: RANSAC Homography Estimation</h3>

A robust homography matrix is computed using **RANSAC (Random Sample Consensus)**, which iteratively identifies the largest set of inlier matches while rejecting outliers caused by noise or mismatches.

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/ransac_image_0.png" alt="RANSAC inliers 0" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/ransac_image_1.png" alt="RANSAC inliers 1" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h3 style="text-align: center;">Step 6: Image Warping & Final Panorama</h3>

The estimated homography warps images into a common coordinate frame. Blending resolves seams at overlap boundaries to produce the final seamless panorama.

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/pano_image_0.png" alt="Panorama result 0" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <img src="https://raw.githubusercontent.com/pvrohin/AutoPano/master/Phase1/Code/Results/Train/Set1/pano_image_1.png" alt="Panorama result 1" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h2 style="text-align: center;">Phase 2: Deep Learning Approach</h2>

Phase 2 replaces the hand-crafted feature pipeline with a **neural network trained to directly predict the homography** between image pairs. Rather than detecting and matching keypoints explicitly, the network learns a mapping from image patches to the 4-point parametrization of the geometric transformation, enabling end-to-end differentiable training.

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/AutoPano" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
