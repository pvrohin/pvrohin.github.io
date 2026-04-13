---
name: Multi-Trailer Autonomous Parking
tools: [Python, Pygame, NumPy, SciPy, A*, RRT, Reeds-Shepp]
image: https://opengraph.githubassets.com/1/pvrohin/multi-trailer-autonomous-parking
description: Path planning and simulation for a truck with multiple trailers navigating a 2D parking lot — using A* and RRT with Reeds-Shepp heuristics and realistic trailer kinematics.
---

<div style="text-align: center;"><h1>Multi-Trailer Autonomous Parking</h1></div>

This project implements **path planning and motion simulation** for a truck with one or more articulated trailers navigating a 2D parking environment with obstacles, developed as a final project for the RBE550 Motion Planning course at **Worcester Polytechnic Institute**. Two planners — **A\*** and **RRT** — are compared on the same task, with realistic multi-trailer kinematics driving both the planning and the Pygame visualization.

---

<h2 style="text-align: center;">The Challenge</h2>

Parking a truck with trailers is significantly harder than planning for a car. Each trailer adds a **coupling constraint** — its orientation relative to the tractor depends on the tractor's steering history. This makes the state space high-dimensional and the dynamics non-holonomic, ruling out simple grid-based planners.

---

<h2 style="text-align: center;">Planning Algorithms</h2>

**A\* Search**

The state space (tractor pose + trailer angles) is discretized into a graph. Transitions are computed from a set of feasible velocity/steering inputs. **Reeds-Shepp paths** are used as the heuristic, estimating the minimum cost to the goal for a car-like system.

**RRT (Rapidly-exploring Random Trees)**

A sampling-based planner that grows a tree from the start by randomly sampling configurations and steering the nearest existing node toward them using kinematic integration. Goal biasing accelerates convergence toward the target parking pose.

**Reeds-Shepp Steering**

Both planners use Reeds-Shepp path lengths as cost estimates. For RRT, Reeds-Shepp paths also serve as the nearest-neighbor steering primitive — the tree expands along the analytically optimal car-like path to the sampled configuration.

---

<h2 style="text-align: center;">Multi-Trailer Kinematics</h2>

The truck-trailer system is modeled as a series of rigid bodies connected by pin joints. At each timestep, the tractor moves according to Ackermann steering equations, and each trailer's orientation is updated using the **trailer angle coupling constraint**:

$$\dot{\psi}_i = \frac{v}{L_i} \sin(\phi_{i-1} - \psi_i)$$

where \\(\psi_i\\) is the i-th trailer's angle, \\(L_i\\) its hitch length, and \\(\phi_{i-1}\\) the preceding body's orientation.

| Component | Method |
|---|---|
| Global planner A | A\* on discretized state space |
| Global planner B | RRT with goal biasing |
| Heuristic / steering | Reeds-Shepp paths |
| Vehicle model | Multi-trailer pin-joint kinematics |
| Visualization | Pygame real-time simulation |

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/multi-trailer-autonomous-parking" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
