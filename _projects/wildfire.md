---
name: WildFire - Autonomous Fire Truck
tools: [Python, PRM, A*, Ackermann Steering, Path Planning, scikit-learn]
image: https://raw.githubusercontent.com/pvrohin/RBE550-WildFire/master/PRM-2.gif
description: Autonomous Ackermann fire truck simulation using PRM global planning and A* local planning to chase and suppress dynamically spreading wildfires in real time.
---

<div style="text-align: center;"><h1>WildFire: Autonomous Fire Truck Simulation</h1></div>

**WildFire** simulates an autonomous **Mercedes fire truck** that must respond to fires ignited by an arsonist and suppress them before they spread to neighboring trees, developed as part of the RBE550 Motion Planning course at **Worcester Polytechnic Institute**. The environment runs in **accelerated time** (1 real second ≈ 5+ simulation seconds), demanding rapid replanning as the fire landscape evolves.

---

<h2 style="text-align: center;">Planning Architecture</h2>

The system uses a **two-layer planning hierarchy** — a global roadmap built once at startup, and a local kinematic planner that queries it at runtime.

**Global Planner: Probabilistic Road Map (PRM)**

At initialization, thousands of random configurations are sampled across the environment and checked for collisions. Valid samples are connected to their nearest neighbors (via a KD-tree for efficient lookup), forming a dense roadmap. When a new fire location is identified, A\* searches the PRM for a collision-free route to that goal.

**Local Planner: A\* with Kinematic Primitives**

The truck steers via **Ackermann steering** (fixed turning radius), so the local planner expands states using a set of kinematic motion primitives that respect the vehicle's non-holonomic constraints. A Euclidean distance heuristic guides the search toward the goal node on the PRM.

---

<h2 style="text-align: center;">PRM Pathfinding Demo</h2>

<div style="text-align: center;">
  <img src="https://raw.githubusercontent.com/pvrohin/RBE550-WildFire/master/PRM-2.gif" alt="PRM pathfinding animation" style="max-width: 700px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

---

<h2 style="text-align: center;">Challenge</h2>

The fire spreads stochastically to adjacent trees over time, requiring the truck to **continuously re-prioritize targets** as the environment changes. A fire left unattended too long can cascade beyond reach, so the planner must balance travel time against suppression urgency — a real-time dynamic replanning problem.

| Component | Method |
|---|---|
| Global roadmap | Probabilistic Road Map (PRM) |
| Graph search | A\* with Euclidean heuristic |
| Nearest-neighbor lookup | KD-tree (scikit-learn) |
| Vehicle model | Ackermann steering |
| Fire spread | Stochastic neighbor propagation |

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/RBE550-WildFire" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
