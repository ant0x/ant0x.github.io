---
layout: home
title: "Antonio Baldi — Threat Intelligence & Hunting"
description: "Analisi tecniche, TTP, IOC e breakdown operativi."
permalink: /
---

<style>
  .hero-card {
    background: linear-gradient(135deg, #0f172a 0%, #1d4ed8 100%);
    color: #f8fafc;
    border-radius: 20px;
    padding: 2rem;
    margin-bottom: 1.5rem;
    box-shadow: 0 12px 35px rgba(15, 23, 42, 0.18);
  }
  .hero-card h1 {
    margin: 0 0 0.5rem 0;
    font-size: 2rem;
  }
  .hero-card p {
    margin: 0.3rem 0;
    line-height: 1.6;
  }
  .hero-links {
    margin-top: 1rem;
    display: flex;
    flex-wrap: wrap;
    gap: 0.7rem;
  }
  .button {
    display: inline-block;
    padding: 0.65rem 1rem;
    border-radius: 999px;
    text-decoration: none;
    font-weight: 600;
  }
  .button.primary {
    background: #f8fafc;
    color: #0f172a;
  }
  .button.secondary {
    background: rgba(255,255,255,0.15);
    color: #f8fafc;
    border: 1px solid rgba(255,255,255,0.25);
  }
  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 1rem;
    margin: 1.2rem 0 1.6rem;
  }
  .info-card {
    background: #ffffff;
    border: 1px solid #e2e8f0;
    border-radius: 16px;
    padding: 1rem;
    box-shadow: 0 6px 20px rgba(15,23,42,0.05);
  }
  .info-card h3 {
    margin-top: 0;
    margin-bottom: 0.4rem;
  }
  .pill-list {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-top: 0.7rem;
  }
  .pill {
    background: #dbeafe;
    color: #1d4ed8;
    padding: 0.3rem 0.6rem;
    border-radius: 999px;
    font-size: 0.9rem;
  }
  .post-list {
    padding-left: 1rem;
  }
  .post-list li { margin-bottom: 0.5rem; }
</style>

<div class="hero-card">
  <p><strong>Cybersecurity Consultant</strong> • Threat Intelligence • Detection Engineering</p>
  <h1>Antonio Baldi</h1>
  <p>Sto costruendo questo spazio come un blog tecnico e personale per condividere analisi, detections, workflow di automazione e riflessioni su sicurezza informatica e SOC.</p>
  <div class="hero-links">
    <a class="button primary" href="/about/">Scopri il profilo</a>
    <a class="button secondary" href="https://github.com/ant0x">Visita GitHub</a>
  </div>
</div>

<div class="card-grid">
  <div class="info-card">
    <h3>Focus attuali</h3>
    <p>Threat hunting, SIEM, cloud security e automazione di risposta.</p>
  </div>
  <div class="info-card">
    <h3>Temi del blog</h3>
    <div class="pill-list">
      <span class="pill">MITRE ATT&CK</span>
      <span class="pill">Sigma</span>
      <span class="pill">SOAR</span>
      <span class="pill">CTI</span>
    </div>
  </div>
  <div class="info-card">
    <h3>Esperienza</h3>
    <p>Consulting in ambito security, detections, IAM e threat intelligence.</p>
  </div>
</div>

## Ultimi articoli
<ul class="post-list">
{% for post in site.posts limit:3 %}
  <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> — {{ post.summary | default: post.excerpt | strip_html | truncate: 140 }}</li>
{% endfor %}
</ul>

## Da dove iniziare
- Leggi l’[About](/about/)
- Esplora i miei progetti su [GitHub](https://github.com/ant0x)
- Se ti interessa il lato operativo, parte dagli articoli su detections e threat hunting

