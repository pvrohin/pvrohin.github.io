---
name: UR30 Image-Based Visual Servoing (ViSP)
tools: [ROS 2 Jazzy, C++, Python, Gazebo, ViSP, MoveIt Servo, OpenCV]
image: /assets/UR30_IBVS/IBVS.gif
description: Eye-in-hand image-based visual servoing on a simulated UR30 workcell — detecting an automotive door panel and servoing on its edge with ViSP and MoveIt Servo.
---

<div style="text-align: center;"><h1>UR30 Image-Based Visual Servoing (ViSP)</h1></div>

---

This project builds a **simulated UR30 workcell with an eye-in-hand Orbbec Gemini 335Lg camera** and an **image-based visual servoing (IBVS)** pipeline on top of it, designed to later run on real hardware. The arm starts in a survey pose above the table, **finds a fixtured automotive door panel** in the camera image, **descends to 0.2 m** above one long edge, and then **servos on that edge**, holding the edge centred in the image while holding a constant standoff. The stack combines **ROS 2 Jazzy**, **Gazebo Harmonic**, **MoveIt Servo**, **ViSP 3.7** and **OpenCV**.

**Code:** [UR30_ROS2_IBVS](https://github.com/pvrohin/UR30_ROS2_IBVS)

---

<h2 style="text-align: center;">Edge-Following IBVS</h2>

<div style="text-align: center;">
  <img src="/assets/UR30_IBVS/IBVS.gif" alt="UR30 image-based visual servoing on a door panel edge" style="max-width: 700px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

---

<h2 style="text-align: center;">Dispensing Lap</h2>

<div style="text-align: center;">
  <img src="/assets/UR30_IBVS/Dispense_Lap.gif" alt="UR30 dispensing lap demonstration" style="max-width: 700px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

---

<h2 style="text-align: center;">System Overview</h2>

**Search**

From a fixed survey pose 0.6 m above the panel, the node thresholds the image for the panel (darker than the table), fits a quadrilateral to its outline and solves PnP. The sub-pixel corners are then **back-projected onto the known table plane** using the exact camera pose from TF, because a near-frontal outline makes the PnP tilt ambiguous (0.3 px of corner noise reads as roughly 2.7° of tilt). The detection is committed after 10 consecutive good frames.

**Approach (look-then-move)**

At 0.2 m the camera sees only a 0.40 × 0.23 m patch, so the full panel outline is no longer visible. The design therefore follows **one long edge**: the node builds a target camera pose 0.2 m above the edge midpoint, looking straight down with the image x-axis along the edge, and steers there with TF-based proportional twists.

**Servo**

The edge is seeded with ViSP's moving-edge tracker (`vpMeLine`), and `vpServo` runs on a single `vpFeatureLine`, restricted to the two degrees of freedom a line constrains: lateral offset and rotation about the optical axis. The standoff is held separately from the TF distance. The resulting camera twist is transformed to the tool frame and sent to **MoveIt Servo**, which drives a joint velocity controller in Gazebo.

---

<h2 style="text-align: center;">State Machine and Fail-Safes</h2>

`WAIT_READY` → `GO_TO_SURVEY` → `SEARCH` → `SWITCH_CONTROL` → `APPROACH` → `SERVO`, with a `FAILED` state reachable from any stage. In `SERVO`, the node gives up and publishes zero twists if no image arrives for 2 s or the tracked edge is missing for 2 s. Failure paths were tested with parameter overrides and fault injection, and every one ended with a stationary camera.

---

<h2 style="text-align: center;">Results</h2>

A multi-case test runner places the panel at random, seeded poses and checks the final camera pose against ground truth from TF, not against anything the IBVS node reports.

- **3 of 3 cases passed** on each of two seeds
- Final camera error of **about 1.4–2.4 mm laterally** and **0.5–0.6 mm in height**, with yaw and tilt near 0°
- Roughly **15–17 s per case** from the start of the survey move to servoing, converging about 0.7 s after entering `SERVO`
- **52 C++ and 11 Python unit tests**, all passing

---

<h2 style="text-align: center;">Package Structure</h2>

| Package | Function |
|---|---|
| `ur30_cell_description` | URDF/xacro for the UR30 workcell |
| `ur30_cell_bringup` | Gazebo world, launch files, RViz config, camera bridges |
| `ur30_cell_moveit_config` | MoveIt Servo configuration |
| `ur30_ibvs` | C++ IBVS node and Python multi-case test runner |

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/UR30_ROS2_IBVS" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
