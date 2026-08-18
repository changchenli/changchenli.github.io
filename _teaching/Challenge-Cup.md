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

<div class="challenge-project__workstream-index">
  <div><span>01</span><strong>True / False Target Recognition</strong><p>Train a compact CNN to distinguish valid targets, false targets, and empty scenes.</p></div>
  <div><span>02</span><strong>Landing-Point Recognition</strong><p>Use feature and geometric validation to locate a trustworthy landing center.</p></div>
</div>

<div class="challenge-project__workstream" id="target-recognition-2024" markdown="1">

<header class="challenge-project__workstream-header">
  <span>2024 WORKSTREAM 01</span>
  <h3>True / False Target Recognition</h3>
  <p>The model classifies each aerial frame into three outcomes: true target, false target, or no target. The presentation emphasizes viewpoint and scale augmentation so recognition remains stable as the aircraft approaches.</p>
</header>

#### Technical Route

<ol class="challenge-project__pipeline">
  <li><span>Dataset</span><strong>9,000+ images</strong><p>Generate multi-angle and multi-scale samples for true and false targets.</p></li>
  <li><span>Encode</span><strong>Four convolution layers</strong><p>Extract progressively higher-level visual features from 150 × 150 RGB input.</p></li>
  <li><span>Compress</span><strong>2 × 2 max pooling</strong><p>Reduce each feature map after convolution to control computation.</p></li>
  <li><span>Optimize</span><strong>Cross-entropy + Adam</strong><p>Train the three-class classifier with a compact optimization setup.</p></li>
  <li><span>Decide</span><strong>Confidence validation</strong><p>Only pass sufficiently confident detections to the landing workflow.</p></li>
</ol>

#### Dataset Construction

<p class="challenge-project__section-note">The training set contains three classes: true target, false target, and no target. Target samples include rotation, position, and scale variation. The no-target class consists of ocean-only images without a target; it is included in training but omitted below to keep the two-column presentation compact.</p>

<div class="challenge-project__dataset-showcase">
  <article>
    <header><span>TRUE TARGET</span><p>Only true targets proceed to the landing-point determination stage.</p></header>
    <div class="challenge-project__dataset-media">
      <img src="{{ '/images/challenge-cup/dataset-true-reference.jpg' | relative_url }}" alt="True-target reference image embedded in the 2024 final presentation" loading="lazy" decoding="async">
      <img src="{{ '/images/challenge-cup/dataset-true-augmentations.png' | relative_url }}" alt="True-target rotation, position, and scale augmentation samples from the 2024 presentation" loading="lazy" decoding="async">
    </div>
    <figure class="challenge-project__dataset-result">
      <img src="{{ '/images/challenge-cup/target-true.gif' | relative_url }}" alt="Animated recognition sequence for a true landing target" loading="lazy" decoding="async">
    </figure>
  </article>
  <article>
    <header><span>FALSE TARGET</span><p>False targets do not proceed to landing-point determination.</p></header>
    <div class="challenge-project__dataset-media">
      <img src="{{ '/images/challenge-cup/dataset-false-reference.png' | relative_url }}" alt="False-target reference image embedded in the 2024 final presentation" loading="lazy" decoding="async">
      <img src="{{ '/images/challenge-cup/dataset-false-augmentations.png' | relative_url }}" alt="False-target rotation, position, and scale augmentation samples from the 2024 presentation" loading="lazy" decoding="async">
    </div>
    <figure class="challenge-project__dataset-result">
      <img src="{{ '/images/challenge-cup/target-false.gif' | relative_url }}" alt="Animated recognition sequence for a false landing target" loading="lazy" decoding="async">
    </figure>
  </article>
</div>

#### Training Configuration

<div class="challenge-project__table-wrap challenge-project__table-wrap--compact" markdown="1">

| Training item | PPT configuration | Portfolio interpretation |
| --- | ---: | --- |
| Training device | GPU preferred; CPU supported | Supports accelerated training and portable execution |
| Maximum epochs | 20 | Compact convergence window used in the reported experiment |
| Batch size | 30 | Mini-batch optimization |
| Learning rate | 0.0001 | Adam optimizer step size |
| Objective | Cross-entropy loss | Three-class classification objective |

</div>

</div>

<div class="challenge-project__workstream" id="landing-recognition-2024" markdown="1">

<header class="challenge-project__workstream-header">
  <span>2024 WORKSTREAM 02</span>
  <h3>Landing-Point Recognition</h3>
  <p>After a true target is confirmed, a second pipeline matches the landing marker, estimates its center, and rejects geometrically implausible regions before a coordinate is released to the flight controller.</p>
</header>

#### Technical Route

<ol class="challenge-project__pipeline challenge-project__pipeline--four">
  <li><span>Match</span><strong>SIFT feature matching</strong><p>Locate the landing marker against a stored reference template.</p></li>
  <li><span>Center</span><strong>Template-center estimate</strong><p>Use the matched region to obtain an initial image-center coordinate.</p></li>
  <li><span>Validate</span><strong>Geometry + color blocks</strong><p>Check the candidate boundary and marker appearance for plausibility.</p></li>
  <li><span>Output</span><strong>Confidence-gated coordinate</strong><p>Publish the landing center only when the validation criteria are satisfied.</p></li>
</ol>

#### Localization Result

<div class="challenge-project__localization-grid">
  <figure>
    <img src="{{ '/images/challenge-cup/landing-geometry-color.gif' | relative_url }}" alt="Animated geometric validation and color-block detection sequence from the 2024 presentation" loading="lazy" decoding="async">
    <figcaption><strong>Geometry and color validation</strong><span>Two complementary checks improve recognition accuracy and stability.</span></figcaption>
  </figure>
  <figure>
    <img src="{{ '/images/challenge-cup/landing-high-altitude.gif' | relative_url }}" alt="Animated landing-target recognition from a higher flight altitude" loading="lazy" decoding="async">
    <figcaption><strong>High-altitude detection</strong><span>Landing-target recognition from a higher flight altitude.</span></figcaption>
  </figure>
  <figure>
    <img src="{{ '/images/challenge-cup/landing-confidence-improved.gif' | relative_url }}" alt="Animated landing-target recognition from a lower flight altitude" loading="lazy" decoding="async">
    <figcaption><strong>Low-altitude detection</strong><span>Refined landing-target recognition from a lower flight altitude.</span></figcaption>
  </figure>
</div>

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
