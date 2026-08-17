---
title: "Challenge Cup · Autonomous UAV Search and Rescue"
excerpt: "Computer-vision, localization, and mission-planning algorithms for autonomous single- and dual-UAV rescue systems."
collection: teaching
type: "Computer Vision Group Leader"
permalink: /teaching/Challenge-Cup/
venue: "National First Prize · 2024"
date: 2024-03-10
location: "Beijing, China"
toc: true
toc_sticky: true
share: false
comments: false
---

<div class="aircraft-project challenge-project" markdown="1">

<p class="aircraft-project__lead">A two-stage research effort in autonomous aerial rescue: a 2024 sea-rescue system combining intelligent flight control with visual target recognition, followed by a 2025 dual-UAV architecture for wide-area search, target localization, and close-range response.</p>

<div class="aircraft-project__facts">
  <div><span>ROLE</span><strong>Computer Vision<br>Algorithm Development</strong></div>
  <div><span>STACK</span><strong>Python · ROS · OpenCV<br>PyTorch · MAVROS</strong></div>
</div>

<div class="challenge-project__hero">
  <figure>
    <img src="{{ '/images/challenge-cup/rescue-red-detection.jpg' | relative_url }}" alt="Processed aerial frame showing a detected red rescue target" fetchpriority="high">
  </figure>
  <div>
    <span>2024 → 2025</span>
    <h2>From visual landing to coordinated rescue</h2>
    <p>The project evolved from single-aircraft target classification and landing-point localization into a coordinated workflow in which a VTOL fixed-wing aircraft searches a large area and passes target coordinates to a quadrotor for close-range response.</p>
  </div>
</div>

## Project Overview

The technical work connects perception, localization, flight control, and inter-aircraft communication into one autonomous mission. Instead of presenting source code directly on this page, the portfolio focuses on the system logic, visual evidence, and measured outcomes; the implementation will be maintained separately on GitHub.

<div class="aircraft-project__principles">
  <article><span>01 / SEARCH</span><h3>Wide-Area Coverage</h3><p>Waypoint planning and VTOL mode control support rapid scanning while respecting restricted areas.</p></article>
  <article><span>02 / PERCEPTION</span><h3>Multi-Stage Vision</h3><p>HSV screening, SIFT descriptors, and Harris corners adapt the pipeline to targets with different colors and textures.</p></article>
  <article><span>03 / LOCALIZATION</span><h3>Geometric Positioning</h3><p>Camera calibration, pose transforms, and geometric validation convert image detections into reliable world coordinates.</p></article>
  <article><span>04 / COORDINATION</span><h3>Dual-UAV Response</h3><p>ROS messaging connects long-range search with precise low-altitude inspection and response.</p></article>
</div>

## 01 · Project Evolution

<div class="challenge-project__evolution">
  <article>
    <span>2024 · NATIONAL FIRST PRIZE</span>
    <h3>Autonomous Sea-Rescue Exploration</h3>
    <p>A single-aircraft workflow combined route planning, fixed-wing and rotary-wing mode transitions, three-class CNN target recognition, SIFT feature matching, and landing-point localization.</p>
    <ul>
      <li>True target / false target / no target classification</li>
      <li>Visual landing-point center estimation</li>
      <li>Confidence and geometric plausibility checks</li>
    </ul>
  </article>
  <article>
    <span>2025 · SECOND ITERATION</span>
    <h3>Dual-UAV Autonomous Search and Rescue</h3>
    <p>A VTOL fixed-wing aircraft performs high-altitude search and publishes target coordinates; a quadrotor then approaches the detected people in mission order for close-range confirmation.</p>
    <ul>
      <li>Red, yellow, and white rescue-target screening</li>
      <li>Restricted-area-aware waypoint execution</li>
      <li>ROS-based coordinate and mission-state exchange</li>
    </ul>
  </article>
</div>

## 02 · Autonomous Mission Workflow

<div class="aircraft-project__sequence challenge-project__mission">
  <div><span>01</span><strong>Search</strong><p>The VTOL aircraft follows a waypoint route to cover the target area efficiently.</p></div>
  <div><span>02</span><strong>Detect</strong><p>Fast color screening narrows the image before feature-level recognition and localization.</p></div>
  <div><span>03</span><strong>Share</strong><p>Validated world coordinates are published through ROS for the response aircraft.</p></div>
  <div><span>04</span><strong>Respond</strong><p>The quadrotor approaches each target and maintains the required low-altitude operating envelope.</p></div>
</div>

### Perception and Localization Pipeline

<ol class="challenge-project__pipeline">
  <li><span>Input</span><strong>Aerial image and vehicle pose</strong><p>Synchronize camera data with the current aircraft state.</p></li>
  <li><span>Screen</span><strong>HSV color filtering</strong><p>Reject empty frames and extract a compact region of interest.</p></li>
  <li><span>Match</span><strong>SIFT or Harris + SIFT</strong><p>Select the feature strategy according to target geometry and imaging conditions.</p></li>
  <li><span>Validate</span><strong>Geometric confidence checks</strong><p>Filter implausible quadrilaterals and unstable center estimates.</p></li>
  <li><span>Transform</span><strong>Pixel to world coordinates</strong><p>Apply the camera model and vehicle pose before publishing the target position.</p></li>
</ol>

## 03 · Visual Recognition Demos

<p class="challenge-project__section-note">These starter assets establish the final media layout. The 2025 detection sequences will later be exported as lightweight web animations and placed in the same frames.</p>

<div class="challenge-project__demo-grid">
  <figure>
    <img src="{{ '/images/challenge-cup/target-true.gif' | relative_url }}" alt="Animated recognition sequence for a true landing target" loading="lazy" decoding="async">
    <figcaption><strong>True-target recognition</strong><span>2024 · CNN classification</span></figcaption>
  </figure>
  <figure>
    <img src="{{ '/images/challenge-cup/target-false.gif' | relative_url }}" alt="Animated recognition sequence for a false landing target" loading="lazy" decoding="async">
    <figcaption><strong>False-target rejection</strong><span>2024 · CNN classification</span></figcaption>
  </figure>
  <figure>
    <img src="{{ '/images/challenge-cup/landing-localization.gif' | relative_url }}" alt="Animated landing-point localization sequence" loading="lazy" decoding="async">
    <figcaption><strong>Landing-point localization</strong><span>2024 · feature matching and center estimation</span></figcaption>
  </figure>
</div>

<div class="challenge-project__detection-strip">
  <figure><img src="{{ '/images/challenge-cup/rescue-red-detection.jpg' | relative_url }}" alt="Detected red rescue target" loading="lazy" decoding="async"><figcaption>Red target</figcaption></figure>
  <figure><img src="{{ '/images/challenge-cup/rescue-yellow-detection.jpg' | relative_url }}" alt="Detected yellow rescue target" loading="lazy" decoding="async"><figcaption>Yellow target</figcaption></figure>
  <figure><img src="{{ '/images/challenge-cup/rescue-white-detection.jpg' | relative_url }}" alt="Detected white rescue target" loading="lazy" decoding="async"><figcaption>White target</figcaption></figure>
</div>

## 04 · Performance Snapshot

<p class="challenge-project__section-note">The table below records the current report-level benchmark. A unified reproducible benchmark will replace it when the public code package is finalized.</p>

<div class="challenge-project__table-wrap" markdown="1">

| Recognition method | Reported processing time | Reported accuracy |
| --- | ---: | ---: |
| High-altitude color recognition | 20–30 ms/frame | >95% |
| Feature matching | 50–60 ms/frame | >98% |
| Hybrid recognition | 30–40 ms/frame | >93% |

</div>

<div class="challenge-project__metrics">
  <div><span>DATASET</span><strong>9,000+</strong><p>Multi-angle and multi-scale training images in the 2024 recognition workflow.</p></div>
  <div><span>OPTIMIZATION</span><strong>3–4×</strong><p>Reported overall image-processing speedup after color pre-screening and ROI reduction.</p></div>
  <div><span>LOCALIZATION</span><strong>−90%</strong><p>Reported reduction in coordinate error in the optimized simulation workflow.</p></div>
</div>

## 05 · Award and Repository

<div class="challenge-project__award">
  <figure>
    <img src="{{ '/images/challenge-cup/award-2024-first-prize.png' | relative_url }}" alt="2024 Challenge Cup national first-prize certificate" loading="lazy" decoding="async">
    <figcaption>19th Challenge Cup · Unveiling and Leading Special Competition · National First Prize</figcaption>
  </figure>
  <div>
    <span>VERIFIED RESULT</span>
    <h3>National First Prize</h3>
    <p>The 2024 project, <em>Deep-Learning-Based Autonomous UAV Exploration and Intelligent Flight Control</em>, received a national first prize in the Challenge Cup special competition.</p>
  </div>
</div>

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
