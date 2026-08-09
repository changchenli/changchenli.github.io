---
title: "2024 China Undergraduate Mathematical Contest in Modeling"
excerpt: "Mathematical modeling and numerical simulation for the Bench Dragon problem."
collection: portfolio
permalink: /portfolio/cumcm-2024/
toc: true
toc_sticky: true
---

*Team Leader · Provincial Third Prize · 2024*

This page presents the structure of our solution to Problem A, **"Bench Dragon"**, in the 2024 China Undergraduate Mathematical Contest in Modeling. Detailed code walkthroughs, figures, and downloadable results will be added progressively.

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

### Problem 3 - Minimum Feasible Spiral Pitch

The dragon must transition from clockwise inward motion to counterclockwise outward motion inside a circular turning region centered at the spiral origin. The region has a diameter of **9 m**. The task is to determine the minimum spiral pitch that allows the front handle of the head to reach the boundary of this turning region without violating the motion constraints.

![Figure 5. Schematic of the turning region]({{ "/images/cumcm-figure-5-turning-region-en.png" | relative_url }})

### Problem 4 - S-Shaped Turning Path

The inward spiral has a pitch of **1.7 m**, and the outward spiral is centrally symmetric to it about the spiral origin. Inside the **9 m-diameter** turning region, the dragon follows an S-shaped path formed by two tangent circular arcs. The radius of the first arc is **twice** that of the second, and both arcs must remain tangent to the relevant spirals. The task also asks whether the arcs can be adjusted to shorten the turning path while preserving tangency.

The front handle of the head moves at **1 m/s**. Positions and velocities for the complete dragon are calculated once per second from **-100 to 100 s**. Representative results are reported at **-100, -50, 0, 50, and 100 s**.

### Problem 5 - Maximum Admissible Head Speed

Following the path defined in Problem 4, determine the maximum constant speed of the head such that the speed of **every handle remains at or below 2 m/s** throughout the motion.

[Back to Experience]({{ "/experience/" | relative_url }})
