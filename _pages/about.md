---
title: "About"
layout: splash
permalink: /about/
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

.about-container{
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
   TAGS
========================= */

.tags{
  display:flex;
  flex-wrap:wrap;
  gap:10px;
}

.tag{
  padding:9px 14px;
  border-radius:999px;
  background:rgba(255,255,255,0.07);
  border:1px solid rgba(255,255,255,0.08);
  color:#eaf4ff;
  font-size:0.84rem;
  line-height:1;
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
  font-size:1.08rem;
  line-height:2;
  color:#d7e7ff;
}

.highlight{
  color:#59c7ff;
  font-weight:700;
}

/* =========================
   CONTENT SECTIONS
========================= */

.content-card{
  padding:40px;
}

.section-title{
  font-size:2rem;
  font-weight:800;
  margin-bottom:28px;
  color:white;
}

.content-text{
  color:#d7e7ff;
  line-height:2;
  font-size:1.03rem;
}

.content-text p{
  margin-bottom:24px;
}

.feature-grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:24px;
  margin-top:24px;
}

.feature-card{
  padding:28px;
  border-radius:22px;
  background:rgba(255,255,255,0.04);
  border:1px solid rgba(255,255,255,0.06);
}

.feature-title{
  color:white;
  font-size:1.2rem;
  font-weight:700;
  margin-bottom:16px;
}

.feature-list{
  color:#d7e7ff;
  line-height:2;
  padding-left:18px;
}

/* =========================
   MOBILE
========================= */

@media(max-width:1200px){

  .about-container{
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
  .content-card{
    padding:28px;
  }

  .hero-title{
    font-size:1.9rem;
    line-height:1.4;
  }

  .name{
    white-space:normal;
    font-size:1.8rem;
  }

  .feature-grid{
    grid-template-columns:1fr;
  }

}

</style>

<div class="about-container">

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

Embedded Systems Engineer focused on system validation, simulation-driven debugging, and reliability analysis for complex real-time industrial systems.

</div>

<div class="sidebar-divider"></div>

<div class="sidebar-title">
Focus Areas
</div>

<div class="tags">

<div class="tag">RTOS</div>
<div class="tag">C/C++</div>
<div class="tag">SILS</div>
<div class="tag">System Validation</div>
<div class="tag">Runtime Analysis</div>
<div class="tag">Integration Testing</div>
<div class="tag">Debugging</div>
<div class="tag">Embedded Systems</div>
<div class="tag">V&V</div>
<div class="tag">Real-Time Systems</div>

</div>

<div class="sidebar-divider"></div>

<div class="sidebar-title">
Interests
</div>

<div class="tags">

<div class="tag">Autonomous Systems</div>
<div class="tag">Safety-Critical Systems</div>
<div class="tag">Simulation Testing</div>
<div class="tag">System Reliability</div>
<div class="tag">Cyber-Physical Systems</div>

</div>

</div>

<!-- MAIN -->

<div class="main">

<div class="hero-card glass">

<div class="hero-title">
Understanding How Real-Time Systems Behave at Runtime
</div>

<div class="hero-text">

I currently work on <span class="highlight">large-scale SMT (Surface Mount Technology) systems</span>, where I contribute to validating and troubleshooting C/C++ based applications operating in real-time and hardware-integrated environments.

My work involves investigating system behavior across software, middleware, motion-control, and hardware interaction layers using simulation-based workflows and structured debugging approaches.

</div>

</div>

<div class="content-card glass">

<div class="section-title">
Engineering Background
</div>

<div class="content-text">

<p>
With over 3 years of experience in embedded and system-level engineering, I have developed strong experience in system-level debugging, simulation-driven validation, integration testing, runtime analysis, and defect reproduction across complex RTOS-based systems.
</p>

<p>
My current role has given me practical exposure to the kinds of reliability and verification challenges found in complex cyber-physical systems — particularly where software behavior must remain stable under tightly coordinated hardware interactions and real-time constraints.
</p>

<p>
While my background comes from industrial automation systems, I am increasingly focused on applying these foundations toward autonomous and intelligent systems testing, especially in areas involving simulation-based validation, safety-critical behavior analysis, software and hardware integration testing, and large-scale embedded system reliability.
</p>

</div>

<div class="feature-grid">

<div class="feature-card">

<div class="feature-title">
Core Engineering Areas
</div>

<ul class="feature-list">
<li>System-level debugging and root cause analysis</li>
<li>Validation and verification of real-time software behavior</li>
<li>Simulation-driven testing and defect reproduction</li>
<li>Integration testing across software and hardware components</li>
<li>Runtime behavior and timing analysis</li>
<li>Large-scale C/C++ embedded systems</li>
</ul>

</div>

<div class="feature-card">

<div class="feature-title">
Current Focus
</div>

<ul class="feature-list">
<li>Autonomous systems validation</li>
<li>Safety-critical system testing</li>
<li>Simulation-based verification workflows</li>
<li>Real-time system reliability engineering</li>
<li>Embedded software architecture analysis</li>
<li>Software-hardware interaction testing</li>
</ul>

</div>

</div>

</div>

<div class="content-card glass">

<div class="section-title">
Engineering Philosophy
</div>

<div class="content-text">

I am particularly interested in roles where system reliability depends on understanding how components behave together at runtime — not only at the code level, but across the broader interaction between software, sensors, control systems, and hardware environments.

This site serves as a structured record of my engineering work and learning. I document debugging cases, testing strategies, architectural insights, and runtime behavior analysis with an emphasis on clarity, reproducibility, and long-term maintainability.

I am actively exploring opportunities in autonomous systems validation and testing, where I can build on my experience in real-time system analysis, simulation-driven debugging, and complex system verification within safety-critical environments.

</div>

</div>

</div>

</div>
