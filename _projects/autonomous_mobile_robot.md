---
name: Autonomous Mobile Robot
tools: [ROS, Python, C++, TurtleBot3, SLAM, Navigation Stack]
image: https://raw.githubusercontent.com/pvrohin/Autonomous-Mobile-Robot/master/SLAM_simulation.png
description: Household autonomous mobile robot built on TurtleBot3 with ROS — featuring teleoperation and SLAM-based autonomous mapping and navigation.
---

<div style="text-align: center;"><h1>Autonomous Mobile Robot</h1></div>

This project develops an **autonomous mobile robot for household use** built on the **TurtleBot3** platform using **ROS (Robot Operating System)**. The system supports two modes of operation: **teleoperation** for remote manual control, and **SLAM-based autonomous navigation** for self-directed map-building and goal-seeking in indoor environments.

---

<h2 style="text-align: center;">SLAM Simulation</h2>

<div style="text-align: center;">
  <img src="https://raw.githubusercontent.com/pvrohin/Autonomous-Mobile-Robot/master/SLAM_simulation.png" alt="SLAM simulation" style="max-width: 700px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

---

<h2 style="text-align: center;">Teleoperation</h2>

<div style="text-align: center;">
  <img src="https://raw.githubusercontent.com/pvrohin/Autonomous-Mobile-Robot/master/Screenshot%202021-03-02%2016.55.58_cropped.png" alt="Teleoperation interface" style="max-width: 700px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

---

<h2 style="text-align: center;">System Overview</h2>

**SLAM (Simultaneous Localization and Mapping)**

The robot uses the `turtlebot3_slam` package to build a 2D occupancy map of its environment in real time using LiDAR scan data. As the robot explores, it simultaneously estimates its own pose within the growing map — the classical chicken-and-egg problem of mobile robotics. The resulting map is used by the navigation stack for autonomous path planning.

**Autonomous Navigation**

Once a map is available, the `turtlebot3_navigation` package enables the robot to receive goal poses and autonomously plan and execute collision-free paths. The ROS navigation stack combines:
- **Global planner** (Dijkstra/A\*) for an initial path on the occupancy map
- **Local planner** (DWA) for real-time obstacle avoidance during execution
- **AMCL** (Adaptive Monte Carlo Localization) for continuous pose estimation within the known map

**Teleoperation**

The `turtlebot3_teleop` package provides keyboard-based manual control, allowing direct velocity commands to be sent to the robot's wheels for testing and data collection.

---

<h2 style="text-align: center;">ROS Package Structure</h2>

| Package | Function |
|---|---|
| `turtlebot3_bringup` | Hardware initialization |
| `turtlebot3_description` | URDF robot model |
| `turtlebot3_slam` | LiDAR-based SLAM |
| `turtlebot3_navigation` | Autonomous path planning + AMCL |
| `turtlebot3_teleop` | Keyboard teleoperation |
| `turtlebot3_simulations` | Gazebo simulation environments |

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/Autonomous-Mobile-Robot" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
