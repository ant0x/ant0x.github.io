---
layout: post
title: "Threat Hunting: un approccio pratico per iniziare"
date: 2026-06-24 13:00:00 +0200
categories: [threathunting, detection]
tags: [threat-hunting, hunting, soc]
author: "ant0x"
summary: "Come avvicinarsi al threat hunting con un metodo semplice, repeatable e orientato ai dati."
---

## Il punto di partenza

Il threat hunting non è solo una questione di strumenti. È una disciplina che combina osservazione, conoscenza del ambiente e capacità di porre domande corrette sui dati disponibili.

## Una metodologia semplice

1. Definire un'ipotesi di attacco o di anomalie.
2. Identificare i dati necessari: endpoint, autenticazioni, DNS, proxy, EDR.
3. Cercare pattern anomali o comportamenti fuori standard.
4. Validare l'ipotesi con contesto operativo.
5. Documentare il risultato e trasformarlo in detections o tuning.

## Esempi di ipotesi utili

- Un utente con privilegi amministrativi esegue attività in orari insoliti.
- Un endpoint genera traffico verso domini nuovi senza precedenti.
- Le autenticazioni da una stessa macchina aumentano improvvisamente in un lasso di tempo ristretto.

## Strumenti che aiutano

- SIEM e log analytics
- EDR con query comportamentali
- Dashboard di rete e DNS
- Pipeline di enrichment IOC

## Conclusione

Il threat hunting funziona meglio quando è guidato da ipotesi chiare e da un buon contesto. Non serve partire da complessi stack tecnologici: spesso il valore nasce da domande semplici ma ben poste.
