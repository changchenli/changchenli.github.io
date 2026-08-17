---
title: "Challenge Cup · Autonomous UAV Search and Rescue"
excerpt: "Computer-vision, localization, and mission-planning algorithms developed across the 2024 and 2025 Challenge Cup competitions."
collection: teaching
type: "Computer Vision Group Leader"
permalink: /teaching/Challenge-Cup/
venue: "Challenge Cup · 2024 / 2025"
date: 2024-03-10
location: "Beijing, China"
toc: true
toc_sticky: true
share: false
comments: false
---

<div class="aircraft-project challenge-project" markdown="1">

<p class="aircraft-project__lead">Two Challenge Cup projects developed in consecutive years. The 2024 entry focused on single-UAV visual recognition and autonomous landing; the 2025 entry extended the work into a dual-UAV search-and-rescue system.</p>

<div class="aircraft-project__facts">
  <div><span>ROLE</span><strong>Computer Vision<br>Algorithm Development</strong></div>
  <div><span>STACK</span><strong>Python · ROS · OpenCV<br>PyTorch · MAVROS</strong></div>
</div>

<nav class="challenge-project__year-nav" aria-label="Challenge Cup project years">
  <a href="#competition-2024"><span>01</span><strong>2024 Competition</strong><small>Single-UAV exploration and visual landing</small></a>
  <a href="#competition-2025"><span>02</span><strong>2025 Competition</strong><small>Dual-UAV autonomous search and rescue</small></a>
</nav>

<section class="challenge-project__year challenge-project__year--2024" id="competition-2024" markdown="1">

<header class="challenge-project__year-header">
  <span>2024 · CHALLENGE CUP</span>
  <h2>Autonomous Sea-Rescue Exploration</h2>
  <p>A single aircraft combined route planning, flight-mode transitions, three-class target recognition, feature matching, and landing-point localization into an autonomous sea-rescue workflow.</p>
</header>

### Project Scope

<div class="aircraft-project__principles">
  <article><span>01 / NAVIGATION</span><h3>Autonomous Exploration</h3><p>Waypoint planning and fixed-wing / rotary-wing transitions supported efficient area coverage and approach.</p></article>
  <article><span>02 / CLASSIFICATION</span><h3>Three-Class CNN</h3><p>The visual model distinguished true landing targets, false targets, and scenes without a target.</p></article>
  <article><span>03 / MATCHING</span><h3>Feature Verification</h3><p>SIFT feature matching verified the target geometry after the initial CNN classification.</p></article>
  <article><span>04 / LANDING</span><h3>Center Localization</h3><p>Geometric checks estimated a stable target center for the autonomous landing stage.</p></article>
</div>

### Recognition and Landing Workflow

<ol class="challenge-project__pipeline challenge-project__pipeline--four">
  <li><span>Input</span><strong>Aerial image</strong><p>Capture the current view during autonomous exploration.</p></li>
  <li><span>Classify</span><strong>Three-class CNN</strong><p>Identify a true target, false target, or empty scene.</p></li>
  <li><span>Verify</span><strong>SIFT matching</strong><p>Confirm the target using local visual features.</p></li>
  <li><span>Localize</span><strong>Landing center</strong><p>Estimate and validate the geometric center used for approach.</p></li>
</ol>

### Visual Results

<div class="challenge-project__demo-grid">
  <figure>
    <img src="{{ '/images/challenge-cup/target-true.gif' | relative_url }}" alt="Animated recognition sequence for a true landing target" loading="lazy" decoding="async">
    <figcaption><strong>True-target recognition</strong><span>CNN classification</span></figcaption>
  </figure>
  <figure>
    <img src="{{ '/images/challenge-cup/target-false.gif' | relative_url }}" alt="Animated recognition sequence for a false landing target" loading="lazy" decoding="async">
    <figcaption><strong>False-target rejection</strong><span>CNN classification</span></figcaption>
  </figure>
  <figure>
    <img src="{{ '/images/challenge-cup/landing-localization.gif' | relative_url }}" alt="Animated landing-point localization sequence" loading="lazy" decoding="async">
    <figcaption><strong>Landing-point localization</strong><span>Feature matching and center estimation</span></figcaption>
  </figure>
</div>

<div class="challenge-project__metrics challenge-project__metrics--single">
  <div><span>TRAINING DATASET</span><strong>9,000+</strong><p>Multi-angle and multi-scale images used in the 2024 recognition workflow.</p></div>
</div>

</section>

<section class="challenge-project__year challenge-project__year--2025" id="competition-2025" markdown="1">

<header class="challenge-project__year-header">
  <span>2025 · CHALLENGE CUP</span>
  <h2>Dual-UAV Autonomous Search and Rescue</h2>
  <p>A VTOL fixed-wing aircraft searched a wide area and published validated target coordinates; a quadrotor then approached the detected people in mission order for close-range response.</p>
</header>

### System Architecture

<div class="challenge-project__hero">
  <figure>
    <img src="{{ '/images/challenge-cup/rescue-red-detection.jpg' | relative_url }}" alt="Processed aerial frame showing a detected red rescue target" loading="lazy" decoding="async">
  </figure>
  <div>
    <span>SEARCH AIRCRAFT → RESPONSE AIRCRAFT</span>
    <h2>Coordinated wide-area rescue</h2>
    <p>The 2025 system separated rapid high-altitude search from precise low-altitude response. ROS messaging connected perception, world-coordinate localization, and mission-state exchange between the two aircraft.</p>
  </div>
</div>

### Autonomous Mission Workflow

<div class="aircraft-project__sequence challenge-project__mission">
  <div><span>01</span><strong>Search</strong><p>The VTOL aircraft follows a restricted-area-aware waypoint route.</p></div>
  <div><span>02</span><strong>Detect</strong><p>Color screening and feature matching identify rescue targets.</p></div>
  <div><span>03</span><strong>Share</strong><p>Validated world coordinates are published through ROS.</p></div>
  <div><span>04</span><strong>Respond</strong><p>The quadrotor approaches each target for close-range action.</p></div>
</div>

### Perception and Localization Pipeline

<ol class="challenge-project__pipeline">
  <li><span>Input</span><strong>Image and vehicle pose</strong><p>Synchronize camera data with the current aircraft state.</p></li>
  <li><span>Screen</span><strong>HSV color filtering</strong><p>Reject empty frames and extract a compact region of interest.</p></li>
  <li><span>Match</span><strong>SIFT or Harris + SIFT</strong><p>Select the feature strategy according to target geometry.</p></li>
  <li><span>Validate</span><strong>Geometric checks</strong><p>Filter implausible contours and unstable center estimates.</p></li>
  <li><span>Transform</span><strong>World coordinates</strong><p>Apply camera and vehicle poses before publishing the target.</p></li>
</ol>

### Detection Results

<div class="challenge-project__detection-strip">
  <figure><img src="{{ '/images/challenge-cup/rescue-red-detection.jpg' | relative_url }}" alt="Detected red rescue target" loading="lazy" decoding="async"><figcaption>Red target</figcaption></figure>
  <figure><img src="{{ '/images/challenge-cup/rescue-yellow-detection.jpg' | relative_url }}" alt="Detected yellow rescue target" loading="lazy" decoding="async"><figcaption>Yellow target</figcaption></figure>
  <figure><img src="{{ '/images/challenge-cup/rescue-white-detection.jpg' | relative_url }}" alt="Detected white rescue target" loading="lazy" decoding="async"><figcaption>White target</figcaption></figure>
</div>

### Performance Snapshot

<p class="challenge-project__section-note">Report-level results from the 2025 perception workflow. A unified reproducible benchmark will replace them when the public code package is finalized.</p>

<div class="challenge-project__table-wrap" markdown="1">

| Recognition method | Reported processing time | Reported accuracy |
| --- | ---: | ---: |
| High-altitude color recognition | 20–30 ms/frame | >95% |
| Feature matching | 50–60 ms/frame | >98% |
| Hybrid recognition | 30–40 ms/frame | >93% |

</div>

<div class="challenge-project__metrics challenge-project__metrics--two">
  <div><span>OPTIMIZATION</span><strong>3–4×</strong><p>Reported image-processing speedup after color pre-screening and ROI reduction.</p></div>
  <div><span>LOCALIZATION</span><strong>−90%</strong><p>Reported reduction in coordinate error in the optimized simulation workflow.</p></div>
</div>

</section>

## 03 · Code Repository

<div class="challenge-project__github">
  <div>
    <span>IMPLEMENTATION</span>
    <h3>Code will live on GitHub</h3>
    <p>The repository will contain the perception, localization, flight-control, and ROS coordination modules together with a compact reproducible example. Large raw datasets and generated frames will remain outside the repository.</p>
  </div>
  <a href="https://github.com/changchenli">View GitHub profile →</a>
</div>

[← Back to Experience]({{ "/experience/" | relative_url }}){: .aircraft-project__back}

</div>
