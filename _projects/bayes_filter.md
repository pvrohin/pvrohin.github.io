---
name: Bayes Filter
tools: [Python, NumPy, Matplotlib, Jupyter Notebook]
image: https://opengraph.githubassets.com/1/pvrohin/Bayes-Filter
description: Discrete Bayes Filter implementation for probabilistic door-state estimation, demonstrating iterative prediction and correction steps for robot state estimation.
---

<div style="text-align: center;"><h1>Bayes Filter</h1></div>

This project implements a **discrete Bayes Filter** for probabilistic state estimation, developed as part of the RBE595 Robot Navigation course at **Worcester Polytechnic Institute**. The system estimates whether a door is **open or closed** by fusing noisy sensor measurements with a probabilistic action model through iterative predict-and-correct cycles.

---

<h2 style="text-align: center;">Algorithm</h2>

The Bayes Filter maintains a belief distribution over all possible states and updates it in two steps at each time instant:

**Prediction Step**

Given the robot's action \\(u_t\\), the prior belief is propagated forward using the motion model:

$$\overline{bel}(x_t) = \sum_{x_{t-1}} p(x_t \mid u_t, x_{t-1}) \cdot bel(x_{t-1})$$

This marginalizes over all possible previous states, weighting each by its probability under the action model.

**Correction Step**

The predicted belief is then updated with the sensor measurement \\(z_t\\):

$$bel(x_t) = \eta \cdot p(z_t \mid x_t) \cdot \overline{bel}(x_t)$$

where \\(\eta\\) is a normalization constant ensuring the distribution sums to 1.

---

<h2 style="text-align: center;">State Estimation Scenarios</h2>

The filter was evaluated across three experimental scenarios:

| Scenario | Actions | Observations | Convergence |
|---|---|---|---|
| Push + open measurement | Push door | Sense open | ~4 iterations to 99.99% |
| Do nothing + closed measurement | No action | Sense closed | ~6 iterations to 99.99% |
| Mixed actions and noisy sensing | Push / no-op | Mixed | ~10 iterations |

In all cases, the filter converges from a **uniform prior** to near-certain belief despite sensor noise, demonstrating the power of recursive Bayesian estimation.

---

<h2 style="text-align: center;">Key Properties</h2>

- **State space**: Binary (door open / door closed)
- **Action model**: Probabilistic push effectiveness (e.g., P(open | push, closed) = 0.8)
- **Sensor model**: Noisy binary observation (e.g., P(sense open | open) = 0.6)
- **Initial belief**: Uniform over all states
- **Implementation**: Pure NumPy in a Jupyter Notebook with inline visualizations

---

<div style="text-align: center;">
  <a href="https://github.com/pvrohin/Bayes-Filter" target="_blank" class="btn btn-dark">
    View Code on GitHub
  </a>
</div>
