---
name: Autonomous Fruit Harvesting Robot
tools: [Python, PyTorch, ROS, Gazebo, OpenCV, Deep Learning]
image: /assets/Fruit_Harvesting_Robot/robot_holding_apple.jpg
description: Autonomous fruit harvesting robot with vision-based detection, segmentation, pose estimation, and ROS-Gazebo simulation.
---

<div style="text-align: center;"><h1>Autonomous Fruit Harvesting Robot</h1></div>

This project is an **autonomous fruit harvesting robot** developed as a collaborative research project between IIT Kanpur and IIT Palakkad. The system uses a mobile platform with a robotic arm and a vision pipeline based on **detection, segmentation, and 3D pose estimation** to locate and pick fruits. The stack was implemented in **Python and ROS**, with simulation in **Gazebo** and **PyBullet**.

---

<h2 style="text-align: center;">Fruit Plucking Robot Architecture</h2>

<div style="text-align: center;">
  <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/Fruit%20Plucking%20Robot%20architecture.jpg" alt="Fruit Plucking Robot architecture" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

---

<h2 style="text-align: center;">Sphere Fitting For Apple Modelling</h2>

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Point Cloud</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/point%20cloud.jpg" alt="Point cloud" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Sphere Fitting</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/sphere_fitting.jpg" alt="Sphere fitting" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h2 style="text-align: center;"><u>Deep Learning Detection Results</u></h2>

<h3 style="text-align: center;">Sample Images In The Collected Dataset</h3>

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/sample_dataset_pic_1.jpg" alt="Sample dataset 1" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/sample_dataset_pic_2.jpg" alt="Sample dataset 2" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

<h3 style="text-align: center;">Mask R-CNN Results On Our Dataset</h3>

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Raw Image</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/Mask_RCNN_Image_Raw_Image.jpg" alt="Mask R-CNN raw image" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Tree and Fruit Localization</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/Mask_RCNN_Image_Result_Image.jpg" alt="Tree and fruit localization" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

<h3 style="text-align: center;">Faster R-CNN Results On Our Dataset</h3>

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/Faster_RCNN_result_1.png" alt="Faster R-CNN result 1" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/Faster_RCNN_result_2.png" alt="Faster R-CNN result 2" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

<h3 style="text-align: center;">YOLO V-5 Results On Our Dataset</h3>

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/Yolo_v5_result_1.jpeg" alt="YOLO v5 result 1" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/Yolo_v5_result_2.jpeg" alt="YOLO v5 result 2" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h2 style="text-align: center;"><u>Fruit Plucking Experiment</u></h2>

<h3 style="text-align: center;">Point Cloud Simulation of Apple tree for Robot Harvesting</h3>

<div class="row">
  <div class="col-md-6 offset-md-3" style="text-align: center;">
    <div class="videoWrapper" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%;">
      <iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/NYbErPjBKk4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>
  </div>
</div>

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Home Position</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/robot_home%20position.jpg" alt="Home position" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Input Image</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/robot_input_image.jpg" alt="Input image" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Fruit Localization</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/robot_input_localization.jpg" alt="Fruit localization" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Fruit Plucking</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/robot_fruit_plucking.jpg" alt="Fruit plucking" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

<div class="row">
  <div class="col-md-6 offset-md-3" style="text-align: center;">
    <p><strong>Robot Holding Apple</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/robot_holding_apple.jpg" alt="Robot holding apple" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

<div class="row">
  <div class="col-md-6 offset-md-3" style="text-align: center;">
    <p><strong>Drop Localization</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/drop_localization.jpg" alt="Drop localization" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h2 style="text-align: center;"><u>Real Time Results</u></h2>

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Test Result Using Captured Image</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/test_result_using_a_captured_image.jpg" alt="Test result using captured image" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>Real Time Result Using ORBBEC Camera</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/real_time_result_using_ORBBEC_camera.jpg" alt="Real time ORBBEC result" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

<div class="row">
  <div class="col-md-6 offset-md-3" style="text-align: center;">
    <p><strong>2D Detected Point And Its Respective 3D Points In Different Frames</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/2D_detected_point_and_its_respective.jpg" alt="2D detected point and 3D points" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

<div class="row">
  <div class="col-md-6 offset-md-3" style="text-align: center;">
    <p><strong>False Detection Scenario</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/false_detection.jpg" alt="False detection" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

<div class="row">
  <div class="col-md-6 offset-md-3" style="text-align: center;">
    <p><strong>Test Result</strong></p>
    <img src="{{ site.baseurl }}/assets/Fruit_Harvesting_Robot/test_result_1.jpg" alt="Test result" style="max-width: 560px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h2 style="text-align: center;">Team</h2>

<div style="text-align: center;">
  <p>Rohin Siddhartha P.V. — perception and simulation</p>
  <p>Dr Radhe Shyam Sharma — control and simulation</p>
  <p>Sandra Cherussery — mechanical design and control</p>
  <p><strong>Faculty:</strong> Dr. Laxmidar Behera, Dr. Santhakumar Mohan</p>
</div>
