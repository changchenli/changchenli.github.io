---
title: "SAIC Motor - Smart Chassis Systems"
permalink: /experience/saic-smart-chassis/
author_profile: true
toc: true
toc_sticky: true
share: false
comments: false
---

<div class="aircraft-project saic-project" markdown="1">

<p class="aircraft-project__lead">A one-month engineering internship focused on smart-chassis mechanical design and simulation, connecting simplified CAD architecture, load-path reasoning, structural optimization, and transmission analysis.</p>

<div class="aircraft-project__facts">
  <div><span>ROLE / PERIOD</span><strong>Engineering Intern · Chassis Dynamics<br>July - August 2025</strong></div>
  <div><span>TOOLS / FOCUS</span><strong>SolidWorks · ANSYS Workbench<br>Corner Module · Worm-Gear Analysis</strong></div>
</div>

## Internship Overview

The internship combined a team design task with an individual simulation study. The team project examined a simplified double-wishbone corner module for uneven-road loading, while the individual task investigated the mechanical response of a worm-and-shaft transmission. Together, the two workstreams formed a compact engineering loop from **geometry and load definition** to **simulation, comparison, and design iteration**.

<div class="aircraft-project__principles">
  <article><span>01 / MODEL</span><h3>Mechanical Architecture</h3><p>Translate reference structures and physical interfaces into a simplified, analysis-ready corner-module assembly.</p></article>
  <article><span>02 / ABSTRACT</span><h3>Load-Path Definition</h3><p>Preserve the key suspension connections and force-transfer paths while removing non-critical geometric detail.</p></article>
  <article><span>03 / OPTIMIZE</span><h3>Structural Iteration</h3><p>Use stress distribution and topology guidance to refine local geometry under a consistent load case.</p></article>
  <article><span>04 / VALIDATE</span><h3>Result Comparison</h3><p>Compare stress, displacement, and mass before and after the structural update.</p></article>
</div>

## 01 · Corner-Module Design and Optimization

The corner-module model was developed from a review of representative architectures, followed by a simplified force diagram and a CAD reconstruction in SolidWorks. The model retained the primary interfaces between the wheel carrier, upper and lower control arms, steering mechanism, and damper so that the main load path remained visible and suitable for finite-element analysis.

<div class="aircraft-project__structure-media">
  <figure>
    <img src="{{ '/images/saic-smart-chassis/corner-module-rotation.gif' | relative_url }}" alt="Animated rotation of the complete corner-module CAD assembly" loading="lazy" decoding="async">
    <figcaption>CAD assembly · Continuous corner-module rotation</figcaption>
  </figure>
  <figure>
    <img src="{{ '/images/saic-smart-chassis/corner-module-exploded.gif' | relative_url }}" alt="Animated exploded view of the corner-module assembly" loading="lazy" decoding="async">
    <figcaption>Assembly structure · Exploded view of the corner-module components</figcaption>
  </figure>
</div>

### Engineering Workflow

<div class="aircraft-project__sequence">
  <div><span>01</span><strong>Architecture research</strong><p>Compare representative layouts and identify the essential suspension and steering interfaces.</p></div>
  <div><span>02</span><strong>CAD simplification</strong><p>Remove non-load-bearing detail while retaining the principal structural members and connection points.</p></div>
  <div><span>03</span><strong>FEA setup</strong><p>Define equivalent loading, constraints, materials, contacts, and local mesh refinement in ANSYS.</p></div>
  <div><span>04</span><strong>Design iteration</strong><p>Use stress concentration and topology results to revise the geometry under the same analysis case.</p></div>
</div>

<div class="saic-project__result-grid">
  <div class="saic-project__metrics">
    <div><span>MAXIMUM STRESS</span><strong>-51.3%</strong><p>Reduction after structural optimization.</p></div>
    <div><span>MASS CHANGE</span><strong>+0.73%</strong><p>Increase relative to the baseline model.</p></div>
  </div>
  <figure>
    <img src="{{ '/images/saic-smart-chassis/topology-optimization.gif' | relative_url }}" alt="Animated topology-optimization result for the corner-module structure" loading="lazy" decoding="async">
    <figcaption>Topology optimization · Material-distribution guidance for structural refinement</figcaption>
  </figure>
</div>

## 02 · Worm-Gear Transmission Analysis

The individual study focused on a worm-and-shaft transmission. After preparing the geometry for analysis, the workflow progressed through meshing, contact and boundary-condition definition, solution checks, and interpretation of stress, strain, and deformation results. The simulation work also supported the construction of a transmission-error curve for comparing the original and processed geometries.

<div class="saic-project__feature">
  <div>
    <span class="saic-project__eyebrow">INDIVIDUAL WORKSTREAM</span>
    <h3>From CAD geometry to mechanical response</h3>
    <p>The analysis was organized around four checkpoints: geometry preparation, mesh quality, load and contact definition, and result interpretation. This created a repeatable structure for isolating solver issues and comparing design changes.</p>
    <ul>
      <li>Prepared the worm-and-shaft assembly for finite-element analysis.</li>
      <li>Evaluated load-induced stress, strain, and deformation.</li>
      <li>Connected simulation output to transmission-error evaluation.</li>
    </ul>
  </div>
  <figure>
    <img src="{{ '/images/saic-smart-chassis/worm-gear-stress.png' | relative_url }}" alt="ANSYS stress result for the worm-and-shaft transmission" loading="lazy" decoding="async">
    <figcaption>ANSYS result · Representative stress distribution in the transmission assembly</figcaption>
  </figure>
</div>

[← Back to Experience]({{ "/experience/" | relative_url }}){: .aircraft-project__back}

</div>
