---
name: Pb-Lite Edge Detection
tools: [Python, OpenCV, NumPy, scikit-learn, Gabor Filters, K-means]
image: https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/1/PbLite_1.png
description: Probability-based edge detection using filter banks, texture/brightness/color gradients, and K-means clustering — outperforming classical Canny and Sobel methods.
---

<div style="text-align: center;"><h1>Pb-Lite Edge Detection</h1></div>

**Pb-Lite** is a simplified implementation of probability-based boundary detection, developed as part of the RBE549 Computer Vision course at **Worcester Polytechnic Institute**. Rather than relying solely on intensity discontinuities, the system incorporates **texture, brightness, and color gradient information** across multiple scales to produce sharper, more semantically meaningful edge maps.

---

<h2 style="text-align: center;">Filter Banks</h2>

Three families of filters are convolved with the input image to extract multi-scale texture responses.

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Derivative of Gaussian (DoG)</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/DoG.png" alt="DoG filter bank" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Leung-Malik (LM) Filters</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/LM.png" alt="LM filter bank" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>
<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Gabor Filters</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/Gabor.png" alt="Gabor filter bank" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Half-Disc (HD) Masks</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/HD.png" alt="Half-disc masks" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h2 style="text-align: center;">Pipeline: Sample Results (Image 1)</h2>

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Original</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/1/Original_1.png" alt="Original image 1" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Texton Map</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/1/TextonMap_1.png" alt="Texton map 1" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>
<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Brightness Map</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/1/BrightnessMap_1.png" alt="Brightness map 1" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Color Map</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/1/ColorMap_1.png" alt="Color map 1" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>
<div class="row">
  <div class="col-md-4" style="text-align: center;">
    <p><strong>Sobel Baseline</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/1/SobelBaseline_1.png" alt="Sobel baseline 1" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-4" style="text-align: center;">
    <p><strong>Canny Baseline</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/1/CannyBaseline_1.png" alt="Canny baseline 1" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-4" style="text-align: center;">
    <p><strong>Pb-Lite Output</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/1/PbLite_1.png" alt="Pb-Lite output 1" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h2 style="text-align: center;">Pipeline: Sample Results (Image 10)</h2>

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Original</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/10/Original_10.png" alt="Original image 10" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Texton Map</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/10/TextonMap_10.png" alt="Texton map 10" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>
<div class="row">
  <div class="col-md-4" style="text-align: center;">
    <p><strong>Sobel Baseline</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/10/SobelBaseline_10.png" alt="Sobel baseline 10" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-4" style="text-align: center;">
    <p><strong>Canny Baseline</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/10/CannyBaseline_10.png" alt="Canny baseline 10" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-4" style="text-align: center;">
    <p><strong>Pb-Lite Output</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE549-Alohomora/master/Phase1/Output/10/PbLite_10.png" alt="Pb-Lite output 10" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h2 style="text-align: center;">How It Works</h2>

**1. Filter Bank Responses** — The input image is convolved with DoG, LM, and Gabor filter banks to generate multi-scale, multi-orientation texture responses.

**2. Texton Map** — K-means clustering (K=64) on filter responses assigns each pixel a texton label, capturing local texture structure.

**3. Brightness & Color Maps** — K-means (K=16) on grayscale intensity and RGB color channels produces compact brightness and color cluster maps.

**4. Gradient Computation** — Half-disc masks at multiple scales compute chi-squared distances between cluster histograms on opposite sides of each pixel, yielding texture gradient (Tg), brightness gradient (Bg), and color gradient (Cg).

**5. Pb-Lite Combination** — The gradients are combined with Sobel and Canny baselines via weighted averaging to produce the final probabilistic boundary map.

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/RBE549-Alohomora" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
