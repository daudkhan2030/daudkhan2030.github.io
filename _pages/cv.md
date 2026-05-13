---
title: "CV"
layout: splash
permalink: /cv/
author_profile: false
classes: wide
---

<style>

/* =========================
   PAGE
========================= */

.page,
.page__content{
  max-width:100% !important;
}

body{
  background:
    radial-gradient(circle at top left, rgba(59,130,246,0.18), transparent 28%),
    radial-gradient(circle at bottom right, rgba(168,85,247,0.16), transparent 28%),
    #06101f;
  color:white;
  font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
}

/* =========================
   LAYOUT
========================= */

.cv-container{
  display:grid;
  grid-template-columns:320px minmax(0,1fr);
  gap:28px;
  align-items:start;
  margin-top:18px;
}

/* =========================
   GLASS CARD
========================= */

.glass{
  background:rgba(255,255,255,0.06);
  border:1px solid rgba(255,255,255,0.08);
  border-radius:28px;
  backdrop-filter:blur(18px);
  -webkit-backdrop-filter:blur(18px);
  box-shadow:
    0 10px 40px rgba(0,0,0,0.35),
    inset 0 1px 0 rgba(255,255,255,0.05);
}

/* =========================
   SIDEBAR
========================= */

.sidebar{
  padding:34px 28px;
  position:sticky;
  top:20px;
  overflow:hidden;
}

.name{
  font-size:2.1rem;
  font-weight:800;
  color:white;
  line-height:1.2;
  letter-spacing:-0.5px;
  white-space:nowrap;
}

.role{
  margin-top:14px;
  color:#5cc8ff;
  font-size:1.15rem;
  font-weight:600;
  line-height:1.7;
}

.summary{
  margin-top:28px;
  color:#d7e7ff;
  line-height:2;
  font-size:1rem;
}

.sidebar-divider{
  height:1px;
  background:rgba(255,255,255,0.08);
  margin:28px 0;
}

.sidebar-title{
  color:#5cc8ff;
  font-size:0.9rem;
  font-weight:700;
  letter-spacing:1px;
  margin-bottom:18px;
  text-transform:uppercase;
}

/* =========================
   SKILLS
========================= */

.skills{
  display:flex;
  flex-wrap:wrap;
  gap:10px;
}

.skill{
  padding:9px 14px;
  border-radius:999px;
  background:rgba(255,255,255,0.07);
  border:1px solid rgba(255,255,255,0.08);
  color:#eaf4ff;
  font-size:0.84rem;
  line-height:1;
}

/* =========================
   LANGUAGES
========================= */

.lang{
  color:#d7e7ff;
  line-height:2;
  font-size:1rem;
}

/* =========================
   MAIN
========================= */

.main{
  display:flex;
  flex-direction:column;
  gap:28px;
}

/* =========================
   HERO
========================= */

.hero-card{
  padding:42px;
}

.hero-title{
  font-size:3rem;
  font-weight:800;
  line-height:1.2;
  margin-bottom:26px;
  color:white;
  letter-spacing:-1px;
}

.hero-text{
  font-size:1.1rem;
  line-height:2;
  color:#d7e7ff;
}

.highlight{
  color:#59c7ff;
  font-weight:700;
}

/* =========================
   TIMELINE
========================= */

.timeline-card{
  padding:40px;
}

.section-title{
  font-size:2.2rem;
  font-weight:800;
  margin-bottom:38px;
  color:white;
}

.timeline{
  position:relative;
}

.timeline:before{
  content:"";
  position:absolute;
  left:114px;
  top:0;
  bottom:0;
  width:2px;
  background:rgba(255,255,255,0.08);
}

.timeline-item{
  display:grid;
  grid-template-columns:90px 1fr;
  gap:46px;
  margin-bottom:44px;
  position:relative;
}

.timeline-date{
  color:#5cc8ff;
  font-weight:700;
  line-height:1.8;
  font-size:1rem;
}

.timeline-content{
  position:relative;
  padding-left:18px;
}

.timeline-content:before{
  content:"";
  width:14px;
  height:14px;
  border-radius:50%;
  background:#4ec6ff;
  position:absolute;
  left:-30px;
  top:9px;
  box-shadow:0 0 18px rgba(78,198,255,0.9);
}

.timeline-content strong{
  display:block;
  color:white;
  font-size:1.25rem;
  margin-bottom:10px;
}

.timeline-content p{
  color:#d7e7ff;
  line-height:1.9;
  font-size:1rem;
  margin:0;
}

/* =========================
   BOTTOM CARDS
========================= */

.bottom-grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:24px;
}

.bottom-card{
  padding:30px;
}

.bottom-title{
  font-size:1.4rem;
  font-weight:700;
  margin-bottom:18px;
  color:white;
}

.bottom-text{
  color:#d7e7ff;
  line-height:1.9;
  font-size:1rem;
}

/* =========================
   MOBILE
========================= */

@media(max-width:1200px){

  .cv-container{
    grid-template-columns:1fr;
  }

  .sidebar{
    position:relative;
    top:0;
  }

  .hero-title{
    font-size:2.3rem;
  }

}

@media(max-width:768px){

  .hero-card,
  .timeline-card,
  .bottom-card{
    padding:28px;
  }

  .hero-title{
    font-size:1.8rem;
    line-height:1.4;
    white-space:normal;
  }

  .name{
    white-space:normal;
    font-size:1.8rem;
  }

  .timeline:before{
    display:none;
  }

  .timeline-item{
    grid-template-columns:1fr;
    gap:10px;
  }

  .timeline-content:before{
    display:none;
  }

  .bottom-grid{
    grid-template-columns:1fr;
  }

}

</style>

<div class="cv-container">

<!-- SIDEBAR -->

<div class="sidebar glass">

<div class="name">
MD Daud Ali Khan
</div>

<div class="role">
Embedded Systems &<br>
Validation Engineer
</div>

<div class="summary">
Embedded Systems Engineer based in Japan with experience in RTOS-based industrial systems, simulation-driven debugging, runtime analysis, and integration testing using C/C++.
</div>

<div class="sidebar-divider"></div>

<div class="sidebar-title">
Core Skills
</div>

<div class="skills">

<div class="skill">C++</div>
<div class="skill">C</div>
<div class="skill">RTOS</div>
<div class="skill">SILS</div>
<div class="skill">System Validation</div>
<div class="skill">Runtime Debugging</div>
<div class="skill">Integration Testing</div>
<div class="skill">Root Cause Analysis</div>
<div class="skill">Middleware</div>
<div class="skill">Visual Studio</div>
<div class="skill">TortoiseSVN</div>

</div>

<div class="sidebar-divider"></div>

<div class="sidebar-title">
Languages
</div>

<div class="lang">Bangla — Native</div>
<div class="lang">English — Fluent</div>
<div class="lang">Japanese — Conversational (JLPT N3)</div>
<div class="lang">Hindi / Urdu — Conversational</div>

</div>

<!-- MAIN -->

<div class="main">

<div class="hero-card glass">

<div class="hero-title">
Building Reliability for Complex Real-Time Systems
</div>

<div class="hero-text">

Currently working on <span class="highlight">large-scale industrial SMT systems</span> involving RTOS-based embedded applications, simulation-driven validation, runtime debugging, and software-hardware integration testing.

My work focuses on understanding how systems behave under real execution conditions — analyzing timing behavior, runtime interactions, defect reproduction, and reliability issues across software and hardware layers.

I am actively transitioning toward roles involving <span class="highlight">autonomous systems testing, V&V, and safety-critical system reliability engineering.</span>

</div>

</div>

<div class="timeline-card glass">

<div class="section-title">
Career Timeline
</div>

<div class="timeline">

<div class="timeline-item">

<div class="timeline-date">
2014 —<br>2018
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
2019 —<br>2021
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
2022 —<br>Present
</div>

<div class="timeline-content">
<strong>Software Engineer — SY System Co., Ltd.</strong>
<p>Embedded C/C++ industrial SMT systems involving SILS validation, runtime debugging, and integration testing in RTOS environments.</p>
</div>

</div>

</div>

</div>

<div class="bottom-grid">

<div class="bottom-card glass">

<div class="bottom-title">
Projects
</div>

<div class="bottom-text">

<strong>Embedded SMT System Development</strong><br><br>

Application-layer development, system validation, runtime debugging, SILS workflows, and integration testing for large-scale industrial systems.

</div>

</div>

<div class="bottom-card glass">

<div class="bottom-title">
Publication
</div>

<div class="bottom-text">

<strong>Kitchen Grocery Items Monitoring System Based on IoT</strong><br><br>

International Journal of Computing and Network Technology (2019)

</div>

</div>

</div>

</div>

</div>
