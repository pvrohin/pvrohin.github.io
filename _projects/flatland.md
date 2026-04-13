---
name: FlatLand - Graph Search Navigation
tools: [Python, BFS, DFS, Dijkstra, Path Planning]
image: https://raw.githubusercontent.com/pvrohin/RBE550-FlatLand/master/performance_plot.png
description: BFS, DFS, Dijkstra, and Random traversal implemented to navigate a point robot through a 2D obstacle field, with performance analysis across coverage levels.
---

<div style="text-align: center;"><h1>FlatLand: Graph Search Navigation</h1></div>

**FlatLand** implements four graph traversal algorithms — **BFS, DFS, Dijkstra, and Random** — to navigate a point robot through a 2D world filled with obstacles, developed as part of the RBE550 Motion Planning course at **Worcester Polytechnic Institute**. The project compares algorithm behavior and performance across environments with varying obstacle coverage densities.

---

<h2 style="text-align: center;">Algorithms</h2>

**Breadth-First Search (BFS)** — Explores nodes layer by layer, guaranteeing the shortest path in terms of number of edges. Effective but memory-intensive in large environments.

**Depth-First Search (DFS)** — Explores as deep as possible before backtracking. Finds a path quickly but does not guarantee optimality.

**Dijkstra's Algorithm** — Weighted graph search that expands nodes in order of cumulative cost, guaranteeing the shortest path in terms of total distance.

**Random Traversal** — Selects neighbors uniformly at random, serving as a baseline to compare against structured search strategies.

---

<h2 style="text-align: center;">Coverage Analysis</h2>

Each algorithm was evaluated across environments with increasing obstacle coverage (5% to 40%), measuring success rate and path quality.

<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>5% Coverage</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE550-FlatLand/master/5_coverage.png" alt="5% coverage" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>10% Coverage</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE550-FlatLand/master/10_coverage.png" alt="10% coverage" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>
<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>20% Coverage</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE550-FlatLand/master/20_coverage.png" alt="20% coverage" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>30% Coverage</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE550-FlatLand/master/30_coverage.png" alt="30% coverage" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>
<div class="row">
  <div class="col-md-6" style="text-align: center;">
    <p><strong>35% Coverage</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE550-FlatLand/master/35_coverage.png" alt="35% coverage" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
  <div class="col-md-6" style="text-align: center;">
    <p><strong>40% Coverage</strong></p>
    <img src="https://raw.githubusercontent.com/pvrohin/RBE550-FlatLand/master/40_coverage.png" alt="40% coverage" style="max-width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
  </div>
</div>

---

<h2 style="text-align: center;">Performance Comparison</h2>

<div style="text-align: center;">
  <img src="https://raw.githubusercontent.com/pvrohin/RBE550-FlatLand/master/performance_plot.png" alt="Performance plot" style="max-width: 700px; width: 100%; height: auto; display: block; margin-left: auto; margin-right: auto;" />
</div>

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/RBE550-FlatLand" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
