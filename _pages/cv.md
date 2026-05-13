---
title: "CV"
layout: splash
permalink: /cv/
author_profile: false
---

<style>

.page__content{
  max-width:1350px !important;
}

/* GLOBAL */

body{
  background:#f5f7fb;
  color:#111827;
  font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
}

.cv-wrapper{
  display:grid;
  grid-template-columns:300px 1fr;
  gap:28px;
  margin-top:20px;
}

/* SIDEBAR */

.sidebar{
  background:#0f172a;
  color:white;
  border-radius:22px;
  padding:28px;
  height:fit-content;
  position:sticky;
  top:20px;
  box-shadow:0 10px 35px rgba(15,23,42,0.15);
}

.name{
  font-size:2.2rem;
  font-weight:800;
  line-height:1.1;
}

.role{
  margin-top:10px;
  color:#38bdf8;
  font-weight:600;
  font-size:1rem;
}

.summary{
  margin-top:20px;
  color:#dbeafe;
  line-height:1.8;
  font-size:0.96rem;
}

.sidebar-section{
  margin-top:30px;
}

.sidebar-title{
  color:#7dd3fc;
  font-size:0.8rem;
  text-transform:uppercase;
  letter-spacing:1px;
  font-weight:700;
  margin-bottom:14px;
}

.skill{
  display:inline-block;
  background:#111827;
  border:1px solid #334155;
  color:#e0f2fe;
  padding:8px 12px;
  border-radius:999px;
  margin:4px;
  font-size:0.82rem;
}

.lang{
  margin-bottom:10px;
  color:#dbeafe;
}

/* MAIN */

.main{
  display:flex;
  flex-direction:column;
  gap:22px;
}

.card{
  background:white;
  border-radius:22px;
  padding:30px;
  border:1px solid #e5e7eb;
  box-shadow:0 6px 22px rgba(15,23,42,0.04);
}

.hero-card{
  background:linear-gradient(135deg,#0f172a,#1e293b);
  color:white;
  border:none;
}

.hero-title{
  font-size:2rem;
  font-weight:800;
  line-height:1.2;
  margin-bottom:16px;
}

.hero-text{
  line-height:1.9;
  color:#dbeafe;
  font-size:1rem;
}

.highlight{
  color:#38bdf8;
  font-weight:700;
}

.section-title{
  font-size:1.3rem;
  font-weight:700;
  margin-bottom:24px;
  color:#0f172a;
}

/* EXPERIENCE */

.exp-item{
  display:grid;
  grid-template-columns:180px 1fr;
  gap:26px;
  padding:22px 0;
  border-bottom:1px solid #e5e7eb;
}

.exp-item:last-child{
  border-bottom:none;
}

.exp-date{
  color:#0284c7;
  font-size:0.92rem;
  font-weight:700;
}

.exp-title{
  font-size:1.05rem;
  font-weight:700;
  margin-bottom:6px;
  color:#111827;
}

.exp-company{
  color:#475569;
  margin-bottom:12px;
  font-size:0.95rem;
}

.exp-desc{
  color:#4b5563;
  line-height:1.8;
}

.exp-desc ul{
  margin-top:10px;
  padding-left:18px;
}

.exp-desc li{
  margin-bottom:8px;
}

/* GRID */

.grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:22px;
}

.small-card{
  background:white;
  border-radius:22px;
  padding:24px;
  border:1px solid #e5e7eb;
  box-shadow:0 6px 22px rgba(15,23,42,0.04);
}

.small-title{
  font-size:1.1rem;
  font-weight:700;
  margin-bottom:16px;
  color:#111827;
}

.small-text{
  color:#4b5563;
  line-height:1.8;
}

/* MOBILE */

@media(max-width:1000px){

  .cv-wrapper{
    grid-template-columns:1fr;
  }

  .sidebar{
    position:relative;
    top:0;
  }

  .exp-item{
    grid-template-columns:1fr;
    gap:8px;
  }

  .grid{
    grid-template-columns:1fr;
  }

}

</style>

<div class="cv-wrapper">

<!-- SIDEBAR -->

<div class="sidebar">

<div class="name">
MD Daud<br>Ali Khan
</div>

<div class="role">
Embedded Systems & Validation Engineer
</div>

<div class="summary">
Embedded Systems Engineer based in Japan with experience in RTOS-based industrial systems, simulation-driven debugging, runtime behavior analysis, and integration testing using C/C++.

Interested in autonomous systems validation, safety-critical verification, and large-scale system reliability engineering.
</div>

<div class="sidebar-section">

<div class="sidebar-title">
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

<div class="sidebar-section">

<div class="sidebar-title">
Languages
</div>

<div class="lang">Bangla — Native</div>
<div class="lang">English — Fluent</div>
<div class="lang">Japanese — Conversational (JLPT N3)</div>
<div class="lang">Hindi / Urdu — Conversational</div>

</div>

</div>

<!-- MAIN -->

<div class="main">

<div class="card hero-card">

<div class="hero-title">
Building Reliability for Complex Real-Time Systems
</div>

<div class="hero-text">

Currently working on <span class="highlight">large-scale industrial SMT systems</span> involving RTOS-based embedded applications, simulation-driven validation, runtime debugging, and software-hardware integration testing.

My work focuses on understanding how systems behave under real execution conditions — analyzing timing behavior, runtime interactions, defect reproduction, and reliability issues across software and hardware layers.

I am actively transitioning toward roles involving <span class="highlight">autonomous systems testing, V&V, and safety-critical system reliability engineering.</span>

</div>

</div>

<div class="card">

<div class="section-title">
Experience & Education
</div>

<div class="exp-item">

<div class="exp-date">
Jul 2022 — Present
</div>

<div>
<div class="exp-title">
Software Engineer
</div>

<div class="exp-company">
SY System Co., Ltd. · Nagoya, Japan
</div>

<div class="exp-desc">

Working on embedded C/C++ industrial SMT systems in RTOS environments.

<ul>
<li>Performed system-level debugging and root cause analysis</li>
<li>Validated runtime behavior using SILS workflows</li>
<li>Executed integration testing across software and hardware layers</li>
<li>Reproduced and analyzed real-world system defects</li>
<li>Worked with large legacy C/C++ codebases and middleware systems</li>
</ul>

</div>
</div>

</div>

<div class="exp-item">

<div class="exp-date">
Jan 2021 — Dec 2021
</div>

<div>
<div class="exp-title">
MIS Executive
</div>

<div class="exp-company">
Rigs Marketing · Dhaka, Bangladesh
</div>

<div class="exp-desc">

Worked on operational analytics, reporting automation, and workflow optimization to support data-driven business decisions.

</div>
</div>

</div>

<div class="exp-item">

<div class="exp-date">
Jan 2019 — Jul 2019
</div>

<div>
<div class="exp-title">
Trainee Developer
</div>

<div class="exp-company">
nazdaqTechnologies · Dhaka, Bangladesh
</div>

<div class="exp-desc">

Worked on Spring Boot backend systems and structured web scraping applications.

</div>
</div>

</div>

<div class="exp-item">

<div class="exp-date">
2019 — 2021
</div>

<div>
<div class="exp-title">
Master of Computer Science
</div>

<div class="exp-company">
American International University-Bangladesh (AIUB)
</div>

<div class="exp-desc">

Completed postgraduate studies and published IoT-based research work.

</div>
</div>

</div>

<div class="exp-item">

<div class="exp-date">
2014 — 2018
</div>

<div>
<div class="exp-title">
Bachelor of Computer Science & Engineering
</div>

<div class="exp-company">
East West University
</div>

<div class="exp-desc">

Focused on algorithms, software engineering, and computer science fundamentals.

</div>
</div>

</div>

</div>

<div class="grid">

<div class="small-card">

<div class="small-title">
Projects
</div>

<div class="small-text">

<strong>Embedded SMT System Development</strong><br><br>

Application-layer development, SILS validation, runtime debugging, integration testing, and system reliability analysis for industrial embedded systems.

</div>

</div>

<div class="small-card">

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
