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

The main numerical conditions include an inward spiral with a pitch of **55 cm**, a prescribed head speed of **1 m/s**, and a simulation interval from **0 to 300 s**. The turning region is a circle with a diameter of **9 m**. For the turning-path problem, the inward spiral has a pitch of **1.7 m**, and the complete motion is evaluated from **-100 to 100 s**. In the final speed-optimization task, the speed of every handle must remain below **2 m/s**.

## Modeling Approach

The solution was organized as a numerical pipeline:

1. Represent the inward and outward paths with Archimedean spirals.
2. Propagate the position of each handle from the dragon head through fixed-distance geometric constraints.
3. Solve nonlinear position equations numerically with `scipy.optimize.fsolve`.
4. Estimate velocities from consecutive time steps.
5. Detect geometric collision between bench sections.
6. Search for feasible pitch, turning-path, and speed parameters.
7. Export full position and velocity histories to Excel for validation.

## Problem Breakdown

### Problem 1 - Position and Velocity Along the Inward Spiral

Compute the position and velocity of the complete dragon from 0 to 300 seconds while the head moves at 1 m/s along a 55 cm-pitch spiral.

**Current modules**

- `位置输出.py` - propagates handle positions and exports `result1.xlsx`
- `速度输出.py` - calculates the velocity of each handle
- `移动可视化.py` - visualizes the time-varying configuration

### Problem 2 - Collision-Limited Termination Time

Determine the latest time at which the dragon can continue moving inward without collision, and record the full state at that instant.

**Current modules**

- `终止时刻判断.py` - performs collision detection and determines the stopping time
- `终止时刻位置记录.py` - exports positions at the limiting state
- `终止时刻速度记录.py` - exports velocities at the limiting state

### Problem 3 - Minimum Feasible Spiral Pitch

Search for the minimum spiral pitch that allows the head to reach the boundary of the 9 m-diameter turning region.

**Current modules**

- `寻找最佳螺距.py` - iteratively searches for a feasible pitch
- `测试不同螺距下模型灵敏度.py` - evaluates sensitivity and convergence
- `不同螺距的收敛所需时间和次数.png` - summarizes the convergence behavior

### Problem 4 - S-Shaped Turning Path

Construct a shorter S-shaped turning path from two tangent circular arcs, connect it smoothly to the inward and outward spirals, and simulate the complete dragon from -100 to 100 seconds.

**Current modules**

- `几何相切路径绘制.py` - constructs the tangent-arc geometry
- `龙头转弯路径绘制.py` - visualizes the head trajectory
- `-100--0s位置输出.py` and `0--100s位置输出.py` - export positions before and after the turning instant
- `-100--0速度输出.py` and `0--100s速度输出.py` - export the corresponding velocities

### Problem 5 - Maximum Admissible Head Speed

Determine the maximum constant head speed such that the speed of every handle remains below 2 m/s.

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
