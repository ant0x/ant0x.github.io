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

<a href="/blog/" class="btn btn--primary">Vedi tutti gli articoli</a>

