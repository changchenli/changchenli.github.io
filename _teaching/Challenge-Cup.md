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

<div class="challenge-project__workstream-index challenge-project__workstream-index--three">
  <div><span>01 · SCREEN</span><strong>High-Altitude Color-Based Screening</strong><p>Pre-localize red, yellow, and white rescue targets during wide-area flight.</p></div>
  <div><span>02 · RECOGNIZE</span><strong>Altitude- and Target-Aware Feature Matching</strong><p>Switch feature strategies as target scale, symmetry, and image detail change.</p></div>
  <div><span>03 · ACCELERATE</span><strong>ROI-Based Hierarchical Acceleration</strong><p>Restrict expensive feature extraction to color-supported image regions.</p></div>
</div>

<ol class="challenge-project__pipeline challenge-project__pipeline--three challenge-project__cv-overview">
  <li><span>HIGH ALTITUDE</span><strong>Color screening</strong><p>Scan the full scene and record candidate positions.</p></li>
  <li><span>LOW ALTITUDE</span><strong>Feature recognition</strong><p>Confirm target identity with local image structure.</p></li>
  <li><span>REAL TIME</span><strong>ROI acceleration</strong><p>Reduce the search area before feature extraction.</p></li>
</ol>

<section class="challenge-project__workstream" id="cv25-high-altitude" markdown="1">

<header class="challenge-project__workstream-header">
  <span>01 · HIGH-ALTITUDE SCREENING</span>
  <h3>High-Altitude Color-Based Screening</h3>
  <p>At flight heights above approximately 50 m, HSV color masks rapidly pre-localized the red, yellow, and white rescue targets. These candidates established the search order and constrained the later low-altitude recognition stage.</p>
</header>

<div class="challenge-project__cv-feature challenge-project__cv-feature--media-wide">
  <figure>
    <img src="{{ '/images/challenge-cup/cv25-high-altitude-screening.gif' | relative_url }}" alt="Alternating raw and processed high-altitude frames showing color-based screening of rescue targets" loading="lazy" decoding="async">
    <figcaption>Original 100 m simulation frames alternate with the color-screening result.</figcaption>
  </figure>
  <div class="challenge-project__cv-notes">
    <span>WIDE-AREA PRE-LOCALIZATION</span>
    <h4>Find candidates before close-range confirmation</h4>
    <p>Color screening is used as a fast first pass rather than the final identity decision. Frames without a supported target color can be rejected before feature matching.</p>
    <ul>
      <li><strong>Red</strong><span>rescue target</span></li>
      <li><strong>Yellow</strong><span>rescue target</span></li>
      <li><strong>White</strong><span>rescue target</span></li>
    </ul>
  </div>
</div>

</section>

<section class="challenge-project__workstream" id="cv25-feature-matching" markdown="1">

<header class="challenge-project__workstream-header">
  <span>02 · ADAPTIVE RECOGNITION</span>
  <h3>Altitude- and Target-Aware Feature Matching</h3>
  <p>Pure SIFT was retained when low-altitude imagery contained sufficient local detail. For blurred high-altitude views and symmetric red or yellow targets, Harris corners supplied stable structural anchors before SIFT description and matching.</p>
</header>

<div class="challenge-project__cv-strategy">
  <div><span>LOW ALTITUDE</span><strong>SIFT</strong><p>Uses rich local texture for direct feature matching.</p></div>
  <div><span>HIGH ALTITUDE / SYMMETRIC TARGET</span><strong>Harris + SIFT</strong><p>Combines boundary-sensitive corners with scale-aware descriptors.</p></div>
</div>

<div class="challenge-project__cv-target-grid">
  <figure><img src="{{ '/images/challenge-cup/cv25-red-feature-matching.gif' | relative_url }}" alt="Red rescue target feature-matching sequence" loading="lazy" decoding="async"><figcaption><strong>Red target</strong><span>Symmetry-aware structural matching</span></figcaption></figure>
  <figure><img src="{{ '/images/challenge-cup/cv25-yellow-feature-matching.gif' | relative_url }}" alt="Yellow rescue target feature-matching sequence" loading="lazy" decoding="async"><figcaption><strong>Yellow target</strong><span>Stable matching across viewpoint change</span></figcaption></figure>
  <figure><img src="{{ '/images/challenge-cup/cv25-white-feature-matching.gif' | relative_url }}" alt="White rescue target feature-matching sequence" loading="lazy" decoding="async"><figcaption><strong>White target</strong><span>Recognition under reduced color contrast</span></figcaption></figure>
</div>

<div class="challenge-project__metrics challenge-project__metrics--two">
  <div><span>OVERALL RECOGNITION</span><strong>&gt;92%</strong><p>Reported recognition accuracy across the adaptive feature-matching workflow.</p></div>
  <div><span>TRUSTED COORDINATES</span><strong>&gt;80%</strong><p>Reported trusted-coordinate ratio under occlusion and low-resolution tests.</p></div>
</div>

</section>

<section class="challenge-project__workstream" id="cv25-roi-acceleration" markdown="1">

<header class="challenge-project__workstream-header">
  <span>03 · HIERARCHICAL ACCELERATION</span>
  <h3>ROI-Based Hierarchical Acceleration</h3>
  <p>The final pipeline combined color pre-screening, bounding-rectangle extraction, conditional downsampling, and feature matching inside the region of interest. This reduced full-frame computation while preserving the target-centered recognition result.</p>
</header>

<ol class="challenge-project__pipeline challenge-project__pipeline--four challenge-project__cv-roi-pipeline">
  <li><span>01</span><strong>Color presence check</strong><p>Skip frames without red, yellow, or white evidence.</p></li>
  <li><span>02</span><strong>Bounding rectangle</strong><p>Extract the minimum target-supported region.</p></li>
  <li><span>03</span><strong>30% area rule</strong><p>Downsample when the ROI exceeds 30% of the full frame.</p></li>
  <li><span>04</span><strong>Local matching</strong><p>Run feature extraction and matching only inside the ROI.</p></li>
</ol>

<div class="challenge-project__cv-comparison">
  <figure><img src="{{ '/images/challenge-cup/cv25-roi-input.jpg' | relative_url }}" alt="Original low-altitude frame before ROI-based feature matching" loading="lazy" decoding="async"><figcaption><span>INPUT</span><strong>Full camera frame</strong></figcaption></figure>
  <figure><img src="{{ '/images/challenge-cup/cv25-roi-matched.jpg' | relative_url }}" alt="Processed low-altitude frame after ROI-based feature matching" loading="lazy" decoding="async"><figcaption><span>OUTPUT</span><strong>Target-centered match</strong></figcaption></figure>
</div>

<div class="challenge-project__table-wrap challenge-project__table-wrap--compact" markdown="1">

| Target class | Before optimization | ROI pipeline | Reported acceleration |
| --- | ---: | ---: | ---: |
| Red / yellow | 120–200 ms | 20–30 ms | 6–8× |
| White | 150–300 ms | 60–80 ms | 2.5–5× |

</div>

<div class="challenge-project__metrics challenge-project__metrics--two">
  <div><span>PROCESSING SPEED</span><strong>3–4×</strong><p>Reported overall acceleration after color screening and ROI reduction.</p></div>
  <div><span>COORDINATE ERROR</span><strong>−90%</strong><p>Reported reduction in coordinate-recognition error after optimization.</p></div>
</div>

</section>

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
