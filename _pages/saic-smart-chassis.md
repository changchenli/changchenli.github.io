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

<div class="saic-project__optimization-story">
  <aside class="saic-project__metrics saic-project__metrics--compact">
    <div><span>MAXIMUM STRESS</span><strong>-19.8%</strong><p>485.61 → 389.25 MPa</p></div>
    <div><span>MASS CHANGE</span><strong>+0.73%</strong><p>Relative to the baseline model</p></div>
  </aside>

  <div class="saic-project__optimization-flow">
    <div class="saic-project__optimization-steps">
      <figure class="saic-project__optimization-card">
        <span class="saic-project__step-label">01 / BASELINE</span>
        <img src="{{ '/images/saic-smart-chassis/knuckle-baseline-stress.png' | relative_url }}" alt="Baseline steering-knuckle stress result with a 20 millimetre lower fillet and rectangular base" loading="lazy" decoding="async">
        <figcaption><strong>20 mm fillet · Rectangular base</strong><p>Peak stress reaches <b>485.61 MPa</b> at the lower fillet.</p></figcaption>
      </figure>

      <div class="saic-project__optimization-bridge">
        <div class="saic-project__optimization-arrow" aria-hidden="true"><span>TOPOLOGY OPTIMIZATION</span><b>→</b></div>
        <figure class="saic-project__optimization-card saic-project__optimization-card--process">
          <div class="saic-project__annotated-result">
            <img src="{{ '/images/saic-smart-chassis/knuckle-topology-process.png' | relative_url }}" alt="Topology-optimization material distribution around the steering-knuckle base and lower fillet" loading="lazy" decoding="async">
            <svg viewBox="0 0 100 100" preserveAspectRatio="none" aria-hidden="true">
              <ellipse cx="58" cy="71" rx="27" ry="16"></ellipse>
              <path d="M27 57 C36 45, 49 42, 63 49"></path>
            </svg>
          </div>
          <figcaption><strong>Material-removal guidance</strong><p>The emerging load path points to two design levers.</p><span class="saic-project__process-tag">Larger fillet</span><span class="saic-project__process-tag">Reshaped base</span></figcaption>
        </figure>
      </div>

      <figure class="saic-project__optimization-card">
        <span class="saic-project__step-label">02 / REFINED</span>
        <img src="{{ '/images/saic-smart-chassis/knuckle-optimized-stress.png' | relative_url }}" alt="Refined steering-knuckle stress result with a 30 millimetre lower fillet and semicircular base" loading="lazy" decoding="async">
        <figcaption><strong>30 mm fillet · Semicircular base</strong><p>Peak stress falls to <b>389.25 MPa</b> at the same critical region.</p></figcaption>
      </figure>
    </div>

    <div class="saic-project__design-response">
      <span>DESIGN RESPONSE</span>
      <p>A larger lower fillet and semicircular base smooth the load transfer path, reducing peak stress by <strong>96.36 MPa (19.8%)</strong>.</p>
    </div>
  </div>
</div>

## 02 · Worm-Gear Transmission Analysis

The individual study focused on a worm-and-shaft transmission. After preparing the geometry for analysis, the workflow progressed through meshing, contact and boundary-condition definition, solution checks, and interpretation of stress, strain, and deformation results. The simulation work also supported the construction of a transmission-error curve for comparing the original and processed geometries.

<div class="saic-project__solver-snapshot">
  <h3>Baseline solver data</h3>
  <table class="saic-project__solver-table">
    <thead><tr><th>Parameter</th><th>Value</th></tr></thead>
    <tbody>
      <tr><td>Mesh nodes</td><td>13,982</td></tr>
      <tr><td>Total elements</td><td>81,344</td></tr>
      <tr><td>SOLID185 elements</td><td>62,956</td></tr>
      <tr><td>Contact elements</td><td>18,384</td></tr>
      <tr><td>Transient window</td><td>1.0 s</td></tr>
      <tr><td>Automatic substeps</td><td>1000 initial · 800 minimum · 1500 maximum</td></tr>
    </tbody>
  </table>
</div>

### Transient Result Fields

<p class="saic-project__results-intro">Four animated views summarize the transient solution, pairing the overall stress and strain fields with close-up tooth-contact responses.</p>

<div class="saic-project__results-gallery">
  <div class="saic-project__results-row saic-project__results-row--mixed">
    <figure>
      <picture>
        <source srcset="{{ '/images/saic-smart-chassis/worm-gear-result-animation-fast.webp' | relative_url }}" type="image/webp">
        <img src="{{ '/images/saic-smart-chassis/worm-gear-result-animation-fast.gif' | relative_url }}" alt="Animated full-assembly worm-gear simulation result cloud map" loading="eager" fetchpriority="high" decoding="async">
      </picture>
      <figcaption><strong>Result overview</strong><span>Full-assembly transient cloud-map animation</span></figcaption>
    </figure>
    <figure>
      <img src="{{ '/images/saic-smart-chassis/worm-gear-stress-contact-slow.gif' | relative_url }}" alt="Animated equivalent stress result at the worm-gear tooth-contact region" loading="lazy" decoding="async">
      <figcaption><strong>Equivalent stress</strong><span>Tooth-contact detail</span></figcaption>
    </figure>
  </div>
  <div class="saic-project__results-row saic-project__results-row--paired">
    <figure>
      <img src="{{ '/images/saic-smart-chassis/worm-gear-strain-overall-slow.gif' | relative_url }}" alt="Animated equivalent elastic strain result for the complete worm-gear assembly" loading="lazy" decoding="async">
      <figcaption><strong>Equivalent elastic strain</strong><span>Full-assembly response</span></figcaption>
    </figure>
    <figure>
      <img src="{{ '/images/saic-smart-chassis/worm-gear-strain-contact-slow.gif' | relative_url }}" alt="Animated equivalent elastic strain result at the worm-gear tooth-contact region" loading="lazy" decoding="async">
      <figcaption><strong>Equivalent elastic strain</strong><span>Tooth-contact detail</span></figcaption>
    </figure>
  </div>
</div>

[← Back to Experience]({{ "/experience/" | relative_url }}){: .aircraft-project__back}

</div>
