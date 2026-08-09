---
title: "2024 China Undergraduate Mathematical Contest in Modeling"
excerpt: "Mathematical modeling and numerical simulation for the Bench Dragon problem."
collection: portfolio
permalink: /portfolio/cumcm-2024/
toc: true
toc_sticky: true
---

*Team Leader · Provincial Third Prize · 2024*

This page presents the structure of our solution to Problem A, **"Bench Dragon"**, in the 2024 China Undergraduate Mathematical Contest in Modeling. Detailed code walkthroughs, figures, and downloadable results will be added progressively. For the implementation code, please visit my [GitHub](https://github.com/changchenli).

## Project Overview

| Item | Details |
| --- | --- |
| Main tools | Python, NumPy, SciPy, Pandas, Matplotlib |
| Core topics | Kinematic modeling, nonlinear equations, collision detection, path design, and constrained optimization |

The dragon specified in the problem consists of **223 benches**: one head bench, **221 body benches**, and one tail bench. The head bench is **341 cm** long, while every body and tail bench is **220 cm** long; all benches are **30 cm** wide. Each bench contains two circular holes with a diameter of **5.5 cm**, and the center of each hole is **27.5 cm** from the nearest end of the bench. Adjacent benches are joined by handles passing through these holes, forming an articulated chain.

![English geometry and connection diagrams for the Bench Dragon]({{ "/images/cumcm-bench-dragon-geometry-en.png" | relative_url }})

## Problem Breakdown

### Problem 1 - Position and Velocity Along the Inward Spiral

The dragon moves clockwise inward along an Archimedean spiral with a pitch of **55 cm**, with the center of every handle constrained to the spiral. The front handle of the head moves at a constant speed of **1 m/s**, starting from point A on the **16th turn**. The task is to calculate the position and velocity of every handle once per second from **0 to 300 s**. The positions and velocities at **0, 60, 120, 180, 240, and 300 s** are also reported for the head, body sections **1, 51, 101, 151, and 201**, and the rear handle of the tail.

#### Representative positions

Values are reported in metres as ordered pairs **(x, y)**.

<div style="overflow-x: auto;" markdown="1">

| Handle | 0 s | 60 s | 120 s | 180 s | 240 s | 300 s |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| Dragon head | (8.800000, 0.000000) | (5.796934, -5.773329) | (-4.090654, -6.300643) | (-2.953259, 6.099638) | (2.578971, -5.363954) | (4.431365, 2.298233) |
| Body section 1 | (8.369181, 2.810104) | (7.446781, -3.461354) | (-1.475517, -7.399592) | (-5.210597, 4.390479) | (4.787614, -3.605656) | (2.527555, 4.362167) |
| Body section 51 | (-9.487335, 1.536473) | (-8.617041, 2.758750) | (-5.334046, 6.550208) | (3.191574, 7.117813) | (5.742258, -4.167273) | (-6.228019, 1.018850) |
| Body section 101 | (2.573780, -10.008907) | (5.352879, -8.224461) | (4.972264, -7.814294) | (1.352935, -8.570071) | (-5.434791, -5.935227) | (-5.712156, 4.649450) |
| Body section 151 | (10.928073, 1.346645) | (7.095125, 7.770906) | (2.995665, 9.552177) | (1.737184, 9.310678) | (3.790548, 8.051313) | (7.564164, 3.384515) |
| Body section 201 | (5.104676, 10.469636) | (-6.056214, 9.406596) | (-10.494961, 2.122963) | (-9.618088, -3.410408) | (-8.087362, -5.311974) | (-8.137016, -4.109661) |
| Rear handle of the tail | (-5.881172, -10.365056) | (6.784539, -9.245707) | (11.000090, 0.012178) | (8.031542, 6.781106) | (4.295605, 9.028862) | (3.148683, 8.918273) |

</div>

#### Representative speeds

Values are reported in metres per second.

<div style="overflow-x: auto;" markdown="1">

| Handle | 0 s | 60 s | 120 s | 180 s | 240 s | 300 s |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| Dragon head | 1.000000 | 1.000000 | 1.000000 | 1.000000 | 1.000000 | 1.000000 |
| Body section 1 | 1.000054 | 1.000065 | 1.000080 | 1.000104 | 1.000145 | 1.000234 |
| Body section 51 | 1.000200 | 1.000254 | 1.000337 | 1.000473 | 1.000721 | 1.001262 |
| Body section 101 | 1.000306 | 1.000387 | 1.000508 | 1.000701 | 1.001042 | 1.001745 |
| Body section 151 | 1.000387 | 1.000485 | 1.000629 | 1.000856 | 1.001246 | 1.002026 |
| Body section 201 | 1.000450 | 1.000561 | 1.000721 | 1.000968 | 1.001387 | 1.002209 |
| Rear handle of the tail | 1.000474 | 1.000589 | 1.000754 | 1.001008 | 1.001436 | 1.002271 |

</div>

<div style="display: flex; gap: 1rem; align-items: flex-start; flex-wrap: wrap; margin: 1rem 0;">
  <figure style="flex: 1 1 320px; min-width: 0; margin: 0;">
    <img src="{{ '/images/cumcm-figure-4-inward-spiral-en.png' | relative_url }}" alt="Figure 4. Schematic of the inward spiral">
  </figure>
  <figure style="flex: 1 1 320px; min-width: 0; margin: 0;">
    <img src="{{ '/images/cumcm-problem1-position-animation.gif' | relative_url }}" alt="Animated position evolution of the Bench Dragon from 0 to 300 seconds">
    <figcaption style="text-align: center;">Position evolution from 0 to 300 s (10 s sampling)</figcaption>
  </figure>
</div>

### Problem 2 - Collision-Limited Termination Time

Using the same inward spiral and motion conditions as Problem 1, determine the latest time at which the dragon can continue moving without any benches colliding. The same representative handles - the head, body sections **1, 51, 101, 151, and 201**, and the rear handle of the tail - are reported separately.

#### Representative results at 412 s

<div style="overflow-x: auto;" markdown="1">

| Handle | x (m) | y (m) | Speed (m/s) |
| --- | ---: | ---: | ---: |
| Dragon head | 0.846985 | 2.143268 | 1.000000 |
| Body section 1 | -1.744999 | 1.659981 | 1.002514 |
| Body section 51 | 2.367861 | 3.813543 | 1.011279 |
| Body section 101 | -2.249786 | -5.430539 | 1.012786 |
| Body section 151 | -1.170048 | -6.899284 | 1.013410 |
| Body section 201 | -7.873807 | 1.181526 | 1.013751 |
| Rear handle of the tail | 3.374615 | 7.638889 | 1.013856 |

</div>

### Problem 3 - Minimum Feasible Spiral Pitch

The dragon must transition from clockwise inward motion to counterclockwise outward motion inside a circular turning region centered at the spiral origin. The region has a diameter of **9 m**. The task is to determine the minimum spiral pitch that allows the front handle of the head to reach the boundary of this turning region without violating the motion constraints.

<div style="display: flex; gap: 1rem; align-items: flex-start; flex-wrap: wrap; margin: 1rem 0;">
  <figure style="flex: 1 1 320px; min-width: 0; margin: 0;">
    <img src="{{ '/images/cumcm-figure-5-turning-region-en.png' | relative_url }}" alt="Figure 5. Schematic of the turning region">
  </figure>
  <figure style="flex: 1 1 320px; min-width: 0; margin: 0;">
    <img src="{{ '/images/cumcm-figure-5-route-result-full.png' | relative_url }}" alt="Simulated Bench Dragon configuration inside the turning region">
  </figure>
</div>

### Problem 4 - S-Shaped Turning Path

The inward spiral has a pitch of **1.7 m**, and the outward spiral is centrally symmetric to it about the spiral origin. Inside the **9 m-diameter** turning region, the dragon follows an S-shaped path formed by two tangent circular arcs. The radius of the first arc is **twice** that of the second, and both arcs must remain tangent to the relevant spirals. The task also asks whether the arcs can be adjusted to shorten the turning path while preserving tangency.

The front handle of the head moves at **1 m/s**. Positions and velocities for the complete dragon are calculated once per second from **-100 to 100 s**. Representative results are reported at **-100, -50, 0, 50, and 100 s**.

### Problem 5 - Maximum Admissible Head Speed

Following the path defined in Problem 4, determine the maximum constant speed of the head such that the speed of **every handle remains at or below 2 m/s** throughout the motion.

[Back to Experience]({{ "/experience/" | relative_url }})

