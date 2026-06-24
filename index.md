---
layout: home
title: "Antonio Baldi — CTI, Threat Hunting & Detection"
description: "Blog personale su cyber threat intelligence, TTP, IOC, detections e automazione SOC."
permalink: /
---

<div class="hero-card">
  <p class="eyebrow">Cyber Threat Intelligence • Detection Engineering • SOC Automation</p>
  <h1>Antonio Baldi</h1>
  <p>Scrivo su CTI, TTP, IOC, detections, threat hunting e automazione operativa per trasformare intelligence in azione concreta.</p>
  <div class="hero-links">
    <a class="button primary" href="/about/">Scopri il profilo</a>
    <a class="button secondary" href="/resources/">Risorse CTI</a>
  </div>
</div>

<div class="card-grid">
  <div class="info-card">
    <h3>CTI in pratica</h3>
    <p>Analisi di campagne, mapping TTP, enrichment IOC, intel reporting e consigli operativi.</p>
  </div>
  <div class="info-card">
    <h3>Temi del blog</h3>
    <div class="pill-list">
      <span class="pill">MITRE ATT&CK</span>
      <span class="pill">Sigma</span>
      <span class="pill">SOAR</span>
      <span class="pill">Threat Hunting</span>
      <span class="pill">IOC</span>
      <span class="pill">CTI</span>
    </div>
  </div>
  <div class="info-card">
    <h3>Focus operativo</h3>
    <p>SIEM, detections, cloud security, identity protection e automazione di incident response.</p>
  </div>
</div>

## Ultimi articoli
<ul class="post-list">
{% for post in site.posts limit:4 %}
  <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> — {{ post.summary | default: post.excerpt | strip_html | truncate: 140 }}</li>
{% endfor %}
</ul>

## Da dove iniziare
- Leggi l’[About](/about/) per capire il mio background
- Esplora le [Risorse](/resources/) CTI e strumenti utili
- Segui gli articoli su detections, TTP e threat hunting se ti interessa il lato operativo

