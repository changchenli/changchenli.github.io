---
title: "Structural and Mechanical Performance of a Trans-Medium Aircraft"
excerpt: "Foldable-wing mechanical architecture and air-water flow-field simulation for a trans-medium aircraft."
collection: teaching
type: "Team Leader · Structural Design"
permalink: /teaching/Undergraduate-Training-Program/
venue: "National-Level Innovation Project"
date: 2024-03-10
location: "Wuhan, China"
toc: true
toc_sticky: true
share: false
comments: false
---

<div class="aircraft-project" markdown="1">

<p class="aircraft-project__lead">A foldable-wing aircraft developed to operate across air and water, where aerodynamic efficiency, underwater drag, water-entry impact, sealing, and structural reliability must be considered as one system.</p>

<div class="aircraft-project__facts">
  <div><span>TOOLS</span><strong>SolidWorks<br>ANSYS · CFD</strong></div>
  <div><span>FOCUS</span><strong>Foldable Wing<br>Air–Water Transition</strong></div>
</div>

## Project Overview

Air rewards low mass and large lifting surfaces. Water, with far greater density and viscosity, demands a compact external shape, sealed electronics, and resistance to severe transient loads. A fixed geometry therefore creates conflicting requirements across the two operating media.

The project addresses this conflict through a servo-driven folding-wing architecture. The wings remain fully deployed during atmospheric flight, then rotate rearward alongside the fuselage before water entry and underwater travel. The project is organized around two main engineering workstreams: **SolidWorks system design** and **flow-field simulation**.

<div class="aircraft-project__principles">
  <article><span>01 / STRUCTURE</span><h3>Lightweight Modular Airframe</h3><p>A high-specific-stiffness fuselage integrates the wing, tail, propulsion system, and sealed electronics bay through serviceable module interfaces.</p></article>
  <article><span>02 / INTEGRATION</span><h3>Watertight System Integration</h3><p>Protected interfaces and an isolated electronics compartment support reliable operation across atmospheric and submerged conditions.</p></article>
  <article><span>03 / TRANSFORMATION</span><h3>Foldable-Wing Mechanism</h3><p>A servo-driven linkage deploys the wing for lift in air and folds it rearward to reduce frontal area and impact loading in water.</p></article>
  <article><span>04 / VALIDATION</span><h3>Cross-Medium Performance Validation</h3><p>Structural response, aerodynamic lift, flow distribution, and water-entry loads are evaluated together to guide design iteration.</p></article>
</div>

## 跨介质飞行器结构

The CAD model separates the aircraft into coordinated fuselage, foldable-wing, tail-control, and propulsion modules. The transformation mechanism is concentrated at the wing root, using a direct transmission path from the servo to the crank arm, linkage, and rotating wing assembly.


<div class="aircraft-project__sequence">
  <div><span>01</span><strong>System layout</strong><p>Define the airframe modules, interfaces, and available installation volume.</p></div>
  <div><span>02</span><strong>Part modeling</strong><p>Build the fuselage, wing-root mechanism, linkages, tail, and sealed compartment.</p></div>
  <div><span>03</span><strong>Assembly validation</strong><p>Check clearances, motion range, connection constraints, and serviceability.</p></div>
  <div><span>04</span><strong>Design iteration</strong><p>Refine the geometry using structural and flow-field simulation feedback.</p></div>
</div>

## 02 · Flow-Field Simulation

The numerical work connects the aircraft geometry to aerodynamic lift, wake development, pressure and velocity distribution, and transient response during the air–water transition. The analysis framework is designed to progressively incorporate boundary conditions, mesh strategy, solver configuration, and configuration comparisons.

### Reference Simulation Parameters

| Parameter | Current reference value |
| --- | ---: |
| Wingspan | 1,110 mm |
| Aircraft length | 1,059 mm |
| Folding range | 0°–75° |
| Reference flight speed | 13 m/s |
| Simulated total lift at reference speed | approximately 35.25 N |

### Analysis Structure

1. **Atmospheric flight:** evaluate lift generation and whole-aircraft external flow.
3. **Water entry:** inspect transient impact loading and the structural response around wing–fuselage interfaces.

[← Back to Experience]({{ "/experience/" | relative_url }}){: .aircraft-project__back}

</div>