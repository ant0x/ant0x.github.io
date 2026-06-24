---
layout: home
title: "Antonio Baldi — CTI, Threat Hunting & Detection"
description: "Blog personale su cyber threat intelligence, threat hunting, detections e SOC automation."
permalink: /
author_profile: true
header:
  overlay_color: "#222"
  overlay_filter: 0.6
---

## Ultimi articoli
{% for post in site.posts limit:6 %}
  {% include archive-single.html type="grid" %}
{% endfor %}

<a href="/#ultimi-articoli" class="btn btn--primary">Vedi tutti gli articoli</a>
<a href="/about/" class="btn btn--secondary" style="margin-left: 1rem;">Chi sono</a>
<a href="/resources/" class="btn btn--secondary" style="margin-left: 1rem;">Risorse</a>

