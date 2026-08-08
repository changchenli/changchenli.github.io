---
permalink: /
title: ""
author_profile: false
classes: wide
redirect_from:
  - /about/
  - /about.html
---

<style>
.page {
  float: none !important;
  width: 100% !important;
  padding-left: 4vw !important;
  padding-right: 4vw !important;
}
.page__inner-wrap,
.page__content {
  float: none !important;
  width: 100% !important;
}
.page__inner-wrap {
  max-width: 1280px;
  margin: 0 auto;
}
.home-shell {
  --home-ink: #1f2933;
  --home-muted: #65717d;
  --home-line: #e5e9ec;
  --home-accent: #237d92;
  --home-soft: #f5f8f9;
  max-width: 1180px;
  margin: 1.5rem auto 4rem;
}
.home-shell * { box-sizing: border-box; }
.home-hero {
  display: grid;
  grid-template-columns: minmax(0, 1fr) 260px;
  gap: clamp(1.5rem, 4vw, 3.5rem);
  align-items: center;
  padding: clamp(1.5rem, 3.5vw, 3.5rem);
  border: 1px solid var(--home-line);
  border-radius: 18px;
  background: linear-gradient(135deg, #fff 0%, var(--home-soft) 100%);
}
.home-eyebrow,
.home-section-label {
  margin: 0 0 1rem;
  color: var(--home-accent);
  font-size: .72rem;
  font-weight: 700;
  letter-spacing: .14em;
  text-transform: uppercase;
}
.home-title {
  margin: 0;
  color: var(--home-ink);
  font-size: clamp(2.6rem, 6vw, 5.2rem);
  line-height: .98;
  letter-spacing: -.05em;
}
.home-role {
  max-width: 660px;
  margin: 1.5rem 0 0;
  color: var(--home-muted);
  font-size: clamp(1rem, 1.5vw, 1.25rem);
  line-height: 1.65;
}
.home-meta {
  display: flex;
  flex-wrap: wrap;
  gap: .6rem;
  margin-top: 1.6rem;
}
.home-meta span {
  padding: .48rem .75rem;
  border: 1px solid var(--home-line);
  border-radius: 999px;
  background: #fff;
  color: #46535e;
  font-size: .76rem;
}
.home-actions {
  display: flex;
  flex-wrap: wrap;
  gap: .75rem;
  margin-top: 2rem;
}
.home-button {
  display: inline-flex;
  align-items: center;
  gap: .75rem;
  padding: .72rem 1rem;
  border: 1px solid var(--home-accent);
  border-radius: 7px;
  color: var(--home-accent) !important;
  font-size: .84rem;
  font-weight: 600;
  text-decoration: none !important;
}
.home-button--primary {
  background: var(--home-accent);
  color: #fff !important;
}
.home-portrait {
  width: 100%;
  aspect-ratio: 3 / 4;
  object-fit: cover;
  border-radius: 12px;
  box-shadow: 0 18px 45px rgba(31, 41, 51, .14);
}
.home-section { margin-top: clamp(3.5rem, 7vw, 5.5rem); }
.home-section-head {
  display: flex;
  justify-content: space-between;
  align-items: end;
  gap: 1rem;
  margin-bottom: 1.25rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid var(--home-line);
}
.home-section-head h2 {
  margin: 0;
  color: var(--home-ink);
  font-size: clamp(1.55rem, 3vw, 2.15rem);
}
.home-section-head p { margin: 0; color: var(--home-muted); font-size: .9rem; }
.interest-grid,
.link-grid {
  display: grid;
  gap: 1rem;
}
.interest-grid { grid-template-columns: repeat(4, minmax(0, 1fr)); }
.interest-card {
  min-height: 180px;
  padding: 1.35rem;
  border: 1px solid var(--home-line);
  border-radius: 12px;
  background: #fff;
}
.interest-card span {
  display: block;
  margin-bottom: 2.4rem;
  color: var(--home-accent);
  font-size: .72rem;
  font-weight: 700;
}
.interest-card h3 {
  margin: 0 0 .6rem;
  color: var(--home-ink);
  font-size: 1.05rem;
}
.interest-card p {
  margin: 0;
  color: var(--home-muted);
  font-size: .82rem;
  line-height: 1.55;
}
.link-grid { grid-template-columns: repeat(3, minmax(0, 1fr)); }
.home-link-card {
  position: relative;
  min-height: 155px;
  padding: 1.35rem;
  border: 1px solid var(--home-line);
  border-radius: 12px;
  color: inherit !important;
  text-decoration: none !important;
  transition: transform .2s ease, border-color .2s ease, box-shadow .2s ease;
}
.home-link-card:hover {
  transform: translateY(-3px);
  border-color: var(--home-accent);
  box-shadow: 0 10px 28px rgba(31, 41, 51, .08);
}
.home-link-card small {
  color: var(--home-accent);
  font-size: .68rem;
  font-weight: 700;
  letter-spacing: .1em;
}
.home-link-card h3 {
  margin: 1.3rem 0 .35rem;
  color: var(--home-ink);
  font-size: 1.15rem;
}
.home-link-card p { margin: 0; color: var(--home-muted); font-size: .82rem; }
.home-link-card b {
  position: absolute;
  right: 1.25rem;
  top: 1.15rem;
  color: var(--home-accent);
  font-size: 1.1rem;
}
@media (max-width: 900px) {
  .interest-grid { grid-template-columns: repeat(2, minmax(0, 1fr)); }
}
@media (max-width: 680px) {
  .home-shell { margin-top: .75rem; }
  .home-hero { grid-template-columns: 1fr; padding: 1.4rem; }
  .home-portrait { grid-row: 1; width: 150px; border-radius: 10px; }
  .home-title { font-size: 2.75rem; }
  .home-section-head { align-items: start; flex-direction: column; }
  .interest-grid,
  .link-grid { grid-template-columns: 1fr; }
  .interest-card { min-height: auto; }
  .interest-card span { margin-bottom: 1.4rem; }
}
</style>

<div class="home-shell">
  <section class="home-hero" aria-labelledby="home-name">
    <div>
      <p class="home-eyebrow">Robotics · Embodied Intelligence</p>
      <h1 class="home-title" id="home-name">Changchen Li</h1>
      <p class="home-role">
        M.Sc. Robotics student at the National University of Singapore,
        building intelligent systems that perceive, learn, and interact
        with the physical world.
      </p>
      <div class="home-meta" aria-label="Profile summary">
        <span>NUS · M.Sc. Robotics</span>
        <span>HUST · Engineering Mechanics</span>
        <span>Singapore</span>
      </div>
      <div class="home-actions">
        <a class="home-button home-button--primary" href="/education/">Education <span>→</span></a>
        <a class="home-button" href="/experience/">Experience <span>→</span></a>
      </div>
    </div>
    <img class="home-portrait" src="/images/self_picture.jpg" alt="Portrait of Changchen Li">
  </section>

  <section class="home-section" aria-labelledby="research-title">
    <div class="home-section-head">
      <div>
        <p class="home-section-label">Research interests</p>
        <h2 id="research-title">What I want to explore</h2>
      </div>
      <p>Intelligence grounded in the physical world.</p>
    </div>
    <div class="interest-grid">
      <article class="interest-card">
        <span>01</span>
        <h3>Robot Learning</h3>
        <p>Learning adaptable robot behaviors from data and interaction.</p>
      </article>
      <article class="interest-card">
        <span>02</span>
        <h3>Embodied AI</h3>
        <p>Connecting perception, reasoning, and action in real environments.</p>
      </article>
      <article class="interest-card">
        <span>03</span>
        <h3>Computer Vision</h3>
        <p>Giving intelligent systems reliable visual understanding.</p>
      </article>
      <article class="interest-card">
        <span>04</span>
        <h3>Multimodal Learning</h3>
        <p>Representations that connect language, vision, and physical signals.</p>
      </article>
    </div>
  </section>

  <section class="home-section" aria-labelledby="explore-title">
    <div class="home-section-head">
      <div>
        <p class="home-section-label">Explore</p>
        <h2 id="explore-title">A clearer path through my work</h2>
      </div>
    </div>
    <div class="link-grid">
      <a class="home-link-card" href="/education/">
        <small>ACADEMIC JOURNEY</small><b>↗</b>
        <h3>Education</h3>
        <p>NUS, HUST, coursework, GPA, and academic honors.</p>
      </a>
      <a class="home-link-card" href="/experience/">
        <small>SELECTED WORK</small><b>↗</b>
        <h3>Experience</h3>
        <p>Competitions, engineering projects, and industry experience.</p>
      </a>
      <a class="home-link-card" href="/assets/Curriculum_Vitae.pdf">
        <small>DOCUMENT</small><b>↗</b>
        <h3>Curriculum Vitae</h3>
        <p>View the complete academic and technical résumé.</p>
      </a>
    </div>
  </section>
</div>
