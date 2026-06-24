---
layout: home
title: "Antonio Baldi — CTI, Threat Hunting & Detection"
description: "Blog personale su cyber threat intelligence, TTP, IOC, detections e automazione SOC."
permalink: /
header:
  overlay_color: "#0f172a"
  overlay_filter: 0.4
  image: /assets/images/avatar.svg
---

<div class="hero-card">
  <p class="eyebrow">Cyber Threat Intelligence • Detection Engineering • SOC Automation</p>
  <h1>Antonio Baldi</h1>
  <p>Questo spazio raccoglie riflessioni, analisi e note tecniche su CTI, TTP, IOC, detections e threat hunting, con l’obiettivo di trasformare l’intelligence in azione concreta.</p>
  <div class="hero-links">
    <a class="button primary" href="/about/">Il mio profilo</a>
    <a class="button secondary" href="/resources/">Risorse CTI</a>
  </div>
</div>

<div class="card-grid">
  <div class="info-card">
    <h3>CTI in pratica</h3>
    <p>Campagne, TTP, IOC, enrichment e report pensati per essere utili a chi lavora in SOC, detections o incident response.</p>
  </div>
  <div class="info-card">
    <h3>Argomenti principali</h3>
    <div class="pill-list">
      <span class="pill">MITRE ATT&CK</span>
      <span class="pill">Sigma</span>
      <span class="pill">Threat Hunting</span>
      <span class="pill">SOAR</span>
      <span class="pill">IOC</span>
      <span class="pill">CTI</span>
    </div>
  </div>
  <div class="info-card">
    <h3>Approccio operativo</h3>
    <p>SIEM, detections, cloud security, identity protection e automazione di risposta agli incidenti.</p>
  </div>
</div>

<div class="home-section">
  <h2>Ultimi articoli</h2>
  <ul class="post-list">
  {% for post in site.posts limit:4 %}
    <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> — {{ post.summary | default: post.excerpt | strip_html | truncate: 140 }}</li>
  {% endfor %}
  </ul>
</div>

<div class="home-section">
  <h2>Per iniziare</h2>
  <ul>
    <li>Leggi l’<a href="/about/">About</a> per capire il mio background</li>
    <li>Esplora le <a href="/resources/">Risorse</a> CTI e gli strumenti più utili</li>
    <li>Segui gli articoli su detections, TTP e threat hunting se ti interessa il lato operativo</li>
  </ul>
</div>

