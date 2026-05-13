---
title: "CV"
layout: splash
permalink: /cv/
author_profile: false
---

<style>

body{
  background:
    radial-gradient(circle at top left, rgba(56,189,248,0.18), transparent 28%),
    radial-gradient(circle at bottom right, rgba(168,85,247,0.18), transparent 28%),
    #0f172a;
}

.page__content{
  max-width:1450px !important;
}

/* MAIN LAYOUT */

.glass-container{
  display:grid;
  grid-template-columns:320px 1fr;
  gap:24px;
  margin-top:20px;
}

/* GLASS EFFECT */

.glass{
  background:rgba(255,255,255,0.08);
  backdrop-filter:blur(18px);
  -webkit-backdrop-filter:blur(18px);
  border:1px solid rgba(255,255,255,0.12);
  box-shadow:0 8px 32px rgba(0,0,0,0.25);
}

/* SIDEBAR */

.sidebar{
  border-radius:28px;
  padding:28px;
  position:sticky;
  top:20px;
  height:fit-content;
}

.name{
  font-size:2.2rem;
  font-weight:800;
  color:#ffffff;
  line-height:1.1;
}

.role{
  margin-top:10px;
  color:#7dd3fc;
  font-size:1rem;
  font-weight:600;
}

.desc{
  margin-top:20px;
  color:#dbeafe;
  line-height:1.8;
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

/* MAIN CONTENT */

.main{
  display:flex;
  flex-direction:column;
  gap:22px;
}

.card{
  border-radius:28px;
  padding:28px;
  color:white;
}

.card-title{
  font-size:1.4rem;
  font-weight:700;
  margin-bottom:22px;
  color:#ffffff;
}

.highlight{
  color:#7dd3fc;
  font-weight:700;
}

/* TIMELINE */

.timeline{
  position:relative;
}

.timeline:before{
  content:"";
  position:absolute;
  left:108px;
  top:0;
  bottom:0;
  width:2px;
  background:rgba(255,255,255,0.12);
}

.timeline-item{
  display:grid;
  grid-template-columns:90px 1fr;
  gap:38px;
  margin-bottom:30px;
  position:relative;
}

.timeline-date{
  color:#7dd3fc;
  font-weight:700;
  font-size:0.9rem;
}

.timeline-content{
  position:relative;
  padding-left:12px;
}

.timeline-content:before{
  content:"";
  width:12px;
  height:12px;
  border-radius:50%;
  background:#38bdf8;
  position:absolute;
  left:-24px;
  top:6px;
  box-shadow:0 0 14px rgba(56,189,248,0.8);
}

.timeline-content strong{
  display:block;
  color:#ffffff;
  margin-bottom:6px;
}

.timeline-content p{
  margin:0;
  color:#dbeafe;
  line-height:1.7;
}

/* GRID */

.grid-2{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:22px;
}

.small-card{
  border-radius:24px;
  padding:22px;
  color:white;
}

.small-title{
  font-size:1.1rem;
  font-weight:700;
  margin-bottom:14px;
  color:#ffffff;
}

.small-text{
  color:#dbeafe;
  line-height:1.8;
}

/* MOBILE */

@media(max-width:1000px){

  .glass-container{
    grid-template-columns:1fr;
  }

  .sidebar{
    position:relative;
    top:0;
  }

  .timeline-item{
    grid-template-columns:1fr;
    gap:8px;
  }

  .timeline:before{
    display:none;
  }

  .timeline-content:before{
    display:none;
  }

  .grid-2{
    grid-template-columns:1fr;
  }

}

</style>

<div class="glass-container">

<!-- SIDEBAR -->

<div class="sidebar glass">

<div class="name">
MD Daud<br>Ali Khan
</div>

<div class="role">
Embedded Systems & Validation Engineer
</div>

<div class="desc">
Embedded Systems Engineer based in Japan working on RTOS-based industrial SMT systems involving simulation-driven debugging, runtime analysis, integration testing, and system-level validation using C/C++.
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

<div class="desc">
Bangla — Native<br>
English — Fluent<br>
Japanese — Conversational (JLPT N3)<br>
Hindi / Urdu — Conversational
</div>

</div>

</div>

<!-- MAIN -->

<div class="main">

<div class="card glass">

<div class="card-title">
Current Focus
</div>

Working on <span class="highlight">large-scale industrial SMT systems</span> involving RTOS-based embedded applications, SILS validation, runtime behavior analysis, and software-hardware integration testing.

Interested in transitioning toward <span class="highlight">autonomous systems validation, safety-critical verification, and complex real-time system reliability engineering.</span>

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
