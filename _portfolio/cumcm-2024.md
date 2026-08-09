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

The dragon moves clockwise inward along an Archimedean spiral with a pitch of **55 cm**, with the center of every handle constrained to the spiral. The front handle of the head moves at a constant speed of **1 m/s**, starting from point A on the **16th turn**. The task is to calculate the position and velocity of every handle once per second from **0 to 300 s** and save the full results in `result1.xlsx`. The positions and velocities at **0, 60, 120, 180, 240, and 300 s** are also reported for the head, body sections **1, 51, 101, 151, and 201**, and the rear handle of the tail.

**Current modules**

- `位置输出.py` - propagates handle positions and exports `result1.xlsx`
- `速度输出.py` - calculates the velocity of each handle
- `移动可视化.py` - visualizes the time-varying configuration

### Problem 2 - Collision-Limited Termination Time

Using the same inward spiral and motion conditions as Problem 1, determine the latest time at which the dragon can continue moving without any benches colliding. The complete position and velocity state at this limiting instant is saved in `result2.xlsx`. The same representative handles - the head, body sections **1, 51, 101, 151, and 201**, and the rear handle of the tail - are reported separately.

**Current modules**

- `终止时刻判断.py` - performs collision detection and determines the stopping time
- `终止时刻位置记录.py` - exports positions at the limiting state
- `终止时刻速度记录.py` - exports velocities at the limiting state

### Problem 3 - Minimum Feasible Spiral Pitch

The dragon must transition from clockwise inward motion to counterclockwise outward motion inside a circular turning region centered at the spiral origin. The region has a diameter of **9 m**. The task is to determine the minimum spiral pitch that allows the front handle of the head to reach the boundary of this turning region without violating the motion constraints.

**Current modules**

- `寻找最佳螺距.py` - iteratively searches for a feasible pitch
- `测试不同螺距下模型灵敏度.py` - evaluates sensitivity and convergence
- `不同螺距的收敛所需时间和次数.png` - summarizes the convergence behavior

### Problem 4 - S-Shaped Turning Path

The inward spiral has a pitch of **1.7 m**, and the outward spiral is centrally symmetric to it about the spiral origin. Inside the **9 m-diameter** turning region, the dragon follows an S-shaped path formed by two tangent circular arcs. The radius of the first arc is **twice** that of the second, and both arcs must remain tangent to the relevant spirals. The task also asks whether the arcs can be adjusted to shorten the turning path while preserving tangency.

The front handle of the head moves at **1 m/s**. Positions and velocities for the complete dragon are calculated once per second from **-100 to 100 s** and saved in `result4.xlsx`. Representative results are reported at **-100, -50, 0, 50, and 100 s**.

**Current modules**

- `几何相切路径绘制.py` - constructs the tangent-arc geometry
- `龙头转弯路径绘制.py` - visualizes the head trajectory
- `-100--0s位置输出.py` and `0--100s位置输出.py` - export positions before and after the turning instant
- `-100--0速度输出.py` and `0--100s速度输出.py` - export the corresponding velocities

### Problem 5 - Maximum Admissible Head Speed

Following the path defined in Problem 4, determine the maximum constant speed of the head such that the speed of **every handle remains at or below 2 m/s** throughout the motion.

**Current module**

- `确定最大行进速度.py` - tests the speed constraint across the full articulated system

## Code Architecture

| Layer | Responsibility | Planned presentation |
| --- | --- | --- |
| Geometry | Spiral, circular-arc, and fixed-distance relations | Equations and diagrams |
| State propagation | Sequential solution of all handle positions | Annotated Python functions |
| Kinematics | Time stepping and velocity estimation | Numerical-method explanation |
| Constraints | Collision and maximum-speed checks | Visual validation examples |
| Optimization | Pitch and speed parameter search | Convergence plots |
| Output | Excel results and trajectory figures | Downloadable data and gallery |

## Results and Visualizations

The existing project files already contain:

- full position and velocity tables for the required time points;
- collision-limited terminal-state results;
- pitch-search convergence analysis;
- inward, turning, and outward trajectory plots;
- frame-by-frame configuration visualizations;
- final Excel outputs for Problems 1, 2, and 4.

This section will next be expanded into a curated results gallery with short explanations instead of publishing every intermediate file.

## Planned Additions

- Selected source code with line-by-line explanations
- Mathematical derivation of the position-propagation model
- Collision-detection diagram
- Interactive or animated trajectory visualization
- Key result tables and convergence plots
- Paper, code, and data download links

[Back to Experience]({{ "/experience/" | relative_url }})
