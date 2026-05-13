---
title: "CV"
layout: splash
permalink: /cv/
author_profile: false
---

<style>

/* ===== PAGE ===== */

.page__content{
  max-width:1400px !important;
}

body{
  background:
    radial-gradient(circle at top left, rgba(56,189,248,0.16), transparent 28%),
    radial-gradient(circle at bottom right, rgba(168,85,247,0.14), transparent 28%),
    #081120;
  color:white;
  font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
}

/* ===== MAIN LAYOUT ===== */

.glass-container{
  display:grid;
  grid-template-columns:minmax(260px,320px) 1fr;
  gap:24px;
  margin-top:20px;
  align-items:start;
}

/* ===== GLASS EFFECT ===== */

.glass{
  background:rgba(255,255,255,0.08);
  backdrop-filter:blur(18px);
  -webkit-backdrop-filter:blur(18px);
  border:1px solid rgba(255,255,255,0.12);
  box-shadow:0 8px 32px rgba(0,0,0,0.25);
}

/* ===== SIDEBAR ===== */

.sidebar{
  border-radius:28px;
  padding:28px;
  position:sticky;
  top:20px;
  height:fit-content;
  overflow:hidden;
}

.name{
  font-size:2.3rem;
  font-weight:800;
  line-height:1.1;
  color:white;
}

.role{
  margin-top:10px;
  color:#7dd3fc;
  font-size:1rem;
  font-weight:600;
  line-height:1.6;
}

.summary{
  margin-top:20px;
  color:#dbeafe;
  line-height:1.9;
  font-size:0.95rem;
}

.section{
  margin-top:28px;
}

.section-title{
  color:#7dd3fc;
  text-transform:uppercase;
  letter-spacing:1px;
  font-size:0.8rem;
  font-weight:700;
  margin-bottom:14px;
}

.skill{
  display:inline-block;
  padding:8px 13px;
  margin:5px;
  border-radius:999px;
  background:rgba(255,255,255,0.08);
  border:1px solid rgba(255,255,255,0.12);
  color:#e0f2fe;
  font-size:0.82rem;
}

.lang{
  margin-bottom:10px;
  color:#dbeafe;
  line-height:1.6;
}

/* ===== MAIN ===== */

.main{
  display:flex;
  flex-direction:column;
  gap:24px;
}

.card{
  border-radius:28px;
  padding:32px;
  color:white;
}

.card-title{
  font-size:1.9rem;
  font-weight:800;
  margin-bottom:20px;
  color:white;
}

.hero-text{
  color:#dbeafe;
  line-height:1.95;
  font-size:1.03rem;
}

.highlight{
  color:#7dd3fc;
  font-weight:700;
}

/* ===== TIMELINE ===== */

.timeline{
  position:relative;
}

.timeline:before{
  content:"";
  position:absolute;
  left:118px;
  top:0;
  bottom:0;
  width:2px;
  background:rgba(255,255,255,0.12);
}

.timeline-item{
  display:grid;
  grid-template-columns:90px 1fr;
  gap:40px;
  margin-bottom:34px;
  position:relative;
}

.timeline-date{
  color:#7dd3fc;
  font-weight:700;
  font-size:0.95rem;
  line-height:1.8;
}

.timeline-content{
  position:relative;
  padding-left:14px;
}

.timeline-content:before{
  content:"";
  width:13px;
  height:13px;
  border-radius:50%;
  background:#38bdf8;
  position:absolute;
  left:-25px;
  top:7px;
  box-shadow:0 0 16px rgba(56,189,248,0.85);
}

.timeline-content strong{
  display:block;
  color:white;
  margin-bottom:8px;
  font-size:1.05rem;
}

.timeline-content p{
  margin:0;
  color:#dbeafe;
  line-height:1.8;
}

/* ===== LOWER GRID ===== */

.grid-2{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:24px;
}

.small-card{
  border-radius:24px;
  padding:24px;
  color:white;
}

.small-title{
  font-size:1.15rem;
  font-weight:700;
  margin-bottom:16px;
  color:white;
}

.small-text{
  color:#dbeafe;
  line-height:1.9;
}

/* ===== MOBILE ===== */

@media(max-width:1200px){

  .glass-container{
    grid-template-columns:1fr;
  }

  .sidebar{
    position:relative;
    top:0;
    width:100%;
  }

}

@media(max-width:768px){

  .timeline:before{
    display:none;
  }

  .timeline-item{
    grid-template-columns:1fr;
    gap:8px;
  }

  .timeline-content:before{
    display:none;
  }

  .grid-2{
    grid-template-columns:1fr;
  }

  .card{
    padding:24px;
  }

  .name{
    font-size:2rem;
  }

  .card-title{
    font-size:1.6rem;
  }

}

</style>

<div class="glass-container">

<!-- ===== SIDEBAR ===== -->

<div class="sidebar glass">

<div class="name">
MD Daud<br>
Ali Khan
</div>

<div class="role">
Embedded Systems & Validation Engineer
</div>

<div class="summary">

Embedded Systems Engineer based in Japan with experience in RTOS-based industrial systems, simulation-driven debugging, runtime analysis, and integration testing using C/C++.

</div>

<div class="section">

<div class="section-title">
Core Skills
</div>

<span class="skill">C++</span>
<span class="skill">C</span>
<span class="skill">RTOS</span>
<span class="skill">SILS</span>
<span class="skill">System Validation</span>
<span class="skill">Runtime Debugging</span>
<span class="skill">Integration Testing</span>
<span class="skill">Root Cause Analysis</span>
<span class="skill">Middleware</span>
<span class="skill">Visual Studio</span>
<span class="skill">TortoiseSVN</span>

</div>

<div class="section">

<div class="section-title">
Languages
</div>

<div class="lang">Bangla — Native</div>
<div class="lang">English — Fluent</div>
<div class="lang">Japanese — Conversational (JLPT N3)</div>
<div class="lang">Hindi / Urdu — Conversational</div>

</div>

</div>

<!-- ===== MAIN ===== -->

<div class="main">

<div class="card glass">

<div class="card-title">
Building Reliability for Complex Real-Time Systems
</div>

<div class="hero-text">

Currently working on <span class="highlight">large-scale industrial SMT systems</span> involving RTOS-based embedded applications, simulation-driven validation, runtime debugging, and software-hardware integration testing.

My work focuses on understanding how systems behave under real execution conditions — analyzing timing behavior, runtime interactions, defect reproduction, and reliability issues across software and hardware layers.

I am actively transitioning toward roles involving <span class="highlight">autonomous systems testing, V&V, and safety-critical system reliability engineering.</span>

</div>

</div>

<div class="card glass">

<div class="card-title">
Career Timeline
</div>

<div class="timeline">

<div class="timeline-item">

<div class="timeline-date">
2014 — 2018
</div>

<div class="timeline-content">
<strong>B.Sc. in Computer Science & Engineering</strong>
<p>East West University — focused on algorithms, software engineering, and core computer science fundamentals.</p>
</div>

</div>

<div class="timeline-item">

<div class="timeline-date">
2019
</div>

<div class="timeline-content">
<strong>Trainee Developer — nazdaqTechnologies</strong>
<p>Worked on Spring Boot backend systems and structured web scraping applications.</p>
</div>

</div>

<div class="timeline-item">

<div class="timeline-date">
2019 — 2021
</div>

<div class="timeline-content">
<strong>M.Sc. in Computer Science</strong>
<p>American International University-Bangladesh (AIUB) with IoT-based research publication.</p>
</div>

</div>

<div class="timeline-item">

<div class="timeline-date">
2021
</div>

<div class="timeline-content">
<strong>MIS Executive — Rigs Marketing</strong>
<p>Worked on reporting automation, operational analytics, and workflow optimization.</p>
</div>

</div>

<div class="timeline-item">

<div class="timeline-date">
2022
</div>

<div class="timeline-content">
<strong>Japanese Language & Career Transition</strong>
<p>Prepared for transition into Japan’s software and embedded systems industry.</p>
</div>

</div>

<div class="timeline-item">

<div class="timeline-date">
2022 — Present
</div>

<div class="timeline-content">
<strong>Software Engineer — SY System Co., Ltd.</strong>
<p>Embedded C/C++ industrial SMT systems involving SILS validation, runtime debugging, and integration testing in RTOS environments.</p>
</div>

</div>

</div>

</div>

<div class="grid-2">

<div class="small-card glass">

<div class="small-title">
Projects
</div>

<div class="small-text">

<strong>Embedded SMT System Development</strong><br><br>

Application-layer development, system validation, runtime debugging, SILS workflows, and integration testing for large-scale industrial systems.

</div>

</div>

<div class="small-card glass">

<div class="small-title">
Publication
</div>

<div class="small-text">

<strong>Kitchen Grocery Items Monitoring System Based on IoT</strong><br><br>

International Journal of Computing and Network Technology (2019)

</div>

</div>

</div>

</div>

</div>
