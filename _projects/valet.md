---
name: Autonomous Valet Parking
tools: [Python, Pygame, NumPy, State Lattice, A*, Path Planning]
image: https://raw.githubusercontent.com/pvrohin/RBE550-Valet/master/images/ackermann_trailer.png
description: State lattice planning with A* for autonomous valet parking — supporting differential drive, Ackermann steering, and truck-trailer vehicle kinematics.
---

<div style="text-align: center;"><h1>Autonomous Valet Parking</h1></div>

**RBE550-Valet** implements **state lattice-based motion planning with A\* search** to navigate three distinct vehicle types through a constrained parking environment with obstacles, developed as part of the RBE550 Motion Planning course at **Worcester Polytechnic Institute**. Each vehicle type operates under unique kinematic constraints reflecting real-world drive mechanics.

---

<h2 style="text-align: center;">Vehicle Types</h2>

<div class="row">
  <div class="col-md-4" style="text-align: center;">
    <p><strong>Differential Drive (Skid Steer)</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE550-Valet/master/source_code/skid.png" alt="Skid steer robot" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-4" style="text-align: center;">
    <p><strong>Ackermann Steering</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE550-Valet/master/source_code/ackermann.png" alt="Ackermann vehicle" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-4" style="text-align: center;">
    <p><strong>Truck + Trailer</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE550-Valet/master/source_code/trailer.png" alt="Truck with trailer" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

<div style="text-align: center; margin-top: 20px;">
  <img src="https://raw.githubusercontent.com/pvrohin/RBE550-Valet/master/images/ackermann_trailer.png" alt="Ackermann trailer path" style="max-width: 700px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

---

<h2 style="text-align: center;">Planning Approach</h2>

**State Lattice** — A structured graph of pre-computed motion primitives is constructed that respects each vehicle's kinematic constraints. Feasible maneuvers (forward, reverse, turning) are encoded as edges between discrete states.

**A\* Search** — The lattice is searched using A\* with a Euclidean distance heuristic. The planner finds the minimum-cost path from start (50, 50) to goal (350, 500) while avoiding rectangular obstacles.

**Collision Detection** — At each expansion step, candidate configurations are checked for intersection with environment obstacles before being added to the search frontier.

| Vehicle | Constraint | Degrees of Freedom |
|---|---|---|
| Differential Drive | Independent wheel speeds | Translation + rotation |
| Ackermann | Fixed turning radius (steering angle) | Non-holonomic, car-like |
| Truck + Trailer | Trailer angle coupling constraint | 3-DOF (truck + trailer angle) |

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/RBE550-Valet" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
