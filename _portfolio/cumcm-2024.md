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
| Competition | China Undergraduate Mathematical Contest in Modeling |
| Problem | 2024 Problem A - "Bench Dragon" |
| Role | Team Leader |
| Award | Provincial Third Prize |
| Main tools | Python, NumPy, SciPy, Pandas, Matplotlib |
| Core topics | Kinematic modeling, nonlinear equations, collision detection, path design, and constrained optimization |

The problem considers a 223-section bench dragon moving along spiral and turning paths. Our objective was to describe the position and velocity of every handle while satisfying rigid geometric, collision, turning-space, and speed constraints.

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
