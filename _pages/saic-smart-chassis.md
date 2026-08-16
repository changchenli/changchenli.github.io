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

### Steering-Knuckle Optimization

<div class="saic-project__optimization-story">
  <aside class="saic-project__metrics saic-project__metrics--compact">
    <div><span>MAXIMUM STRESS</span><strong>-51.3%</strong><p>485.61 → 236.35 MPa</p></div>
    <div><span>COMPONENT MASS</span><strong>-65.6%</strong><p><b>Q345:</b> 13.671 → 13.771 kg (+0.73%)<br><b>A6061:</b> 4.7 kg (-65.6% from baseline)</p></div>
  </aside>

  <div class="saic-project__optimization-flow">
    <div class="saic-project__phase-heading">
      <span>PHASE 01</span>
      <strong>Topology-guided geometry screening</strong>
      <p>The first pass identified the lower fillet and base profile as the two practical design levers.</p>
    </div>

    <div class="saic-project__optimization-steps saic-project__optimization-steps--screening">
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
        <span class="saic-project__step-label">02 / FIRST REFINEMENT</span>
        <img src="{{ '/images/saic-smart-chassis/knuckle-optimized-stress.png' | relative_url }}" alt="Refined steering-knuckle stress result with a 30 millimetre lower fillet and semicircular base" loading="lazy" decoding="async">
        <figcaption><strong>30 mm fillet · Semicircular base</strong><p>The best screened geometry reduces peak stress to <b>389.25 MPa</b>.</p></figcaption>
      </figure>
    </div>

    <div class="saic-project__iteration-drop" aria-hidden="true"><span>ITERATE THE LOAD PATH</span><b>↓</b></div>

    <div class="saic-project__phase-heading">
      <span>PHASE 02</span>
      <strong>Thickness and transition refinement</strong>
      <p>Two further revisions removed the remaining stress concentration and brought the design below the Q345 yield limit.</p>
    </div>

    <div class="saic-project__optimization-steps saic-project__optimization-steps--iteration">
      <figure class="saic-project__optimization-card saic-project__optimization-card--iteration">
        <span class="saic-project__step-label">03 / BASE THICKNESS</span>
        <div class="saic-project__iteration-media">
          <img src="{{ '/images/saic-smart-chassis/knuckle-thickened-stress.png' | relative_url }}" alt="ANSYS stress result after increasing the steering-knuckle base thickness to 30 millimetres" loading="lazy" decoding="async">
        </div>
        <figcaption><strong>Increase base thickness · 20 → 30 mm</strong><p>Peak stress falls from 389.25 to <b>265.84 MPa</b>; the critical region shifts to the side-plate corner.</p></figcaption>
      </figure>

      <div class="saic-project__iteration-arrow" aria-hidden="true"><span>SMOOTH CORNER</span><b>→</b></div>

      <figure class="saic-project__optimization-card saic-project__optimization-card--iteration saic-project__optimization-card--final">
        <span class="saic-project__step-label">04 / FINAL DESIGN</span>
        <div class="saic-project__iteration-media">
          <img src="{{ '/images/saic-smart-chassis/knuckle-final-hotspot.png' | relative_url }}" alt="Final ANSYS stress close-up showing 236.35 megapascal maximum stress at the lower-control-arm hole connection" loading="lazy" decoding="async">
        </div>
        <figcaption><strong>Smooth the side-plate corner</strong><p>Peak stress reaches <b>236.35 MPa</b>, now concentrated at the lower-control-arm hole connection.</p></figcaption>
      </figure>
    </div>

    <div class="saic-project__stress-route" aria-label="Peak stress progression from baseline to final design">
      <span><b>485.61</b><small>Baseline</small></span><i>→</i>
      <span><b>389.25</b><small>Geometry</small></span><i>→</i>
      <span><b>265.84</b><small>Thickness</small></span><i>→</i>
      <span class="is-final"><b>236.35 MPa</b><small>Final</small></span>
    </div>

    <div class="saic-project__mass-route" aria-label="Component mass progression from the baseline Q345 structure to the A6061 final design">
      <span><b>13.671 kg</b><small>Q345 · Baseline</small></span><i>→</i>
      <span><b>13.771 kg</b><small>Q345 · Optimized geometry</small><em>+0.73%</em></span><i>→</i>
      <span class="is-final"><b>4.7 kg</b><small>A6061 · Material substitution</small><em>-65.6%</em></span>
    </div>

    <div class="saic-project__design-response">
      <span>DESIGN DECISION</span>
      <p>A reinforcing-rib trial was rejected because it raised peak stress to <strong>604.91 MPa</strong>. The selected geometry instead combines a 30 mm fillet, semicircular 30 mm base, and smooth side-plate transition; an A6061 material substitution then reduces component mass to <strong>4.7 kg</strong>.</p>
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
