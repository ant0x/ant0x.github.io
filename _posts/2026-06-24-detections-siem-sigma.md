---
layout: post
title: "Come strutturare detections SIEM con Sigma"
date: 2026-06-24 12:00:00 +0200
categories: [soc, detections]
tags: [sigma, siem, detection-engineering]
author: "ant0x"
summary: "Una guida pratica per organizzare detections riconoscibili, portabili e facili da mantenere."
---

## Perché Sigma

Sigma è diventato uno standard molto utile per descrivere regole di rilevamento in modo indipendente dal motore di sicurezza utilizzato. Il vantaggio principale è la possibilità di scrivere una regola una volta e poi riusarla su diversi SIEM, EDR o piattaforme di log management.

## Struttura di una regola semplice

Una regola Sigma è normalmente composta da:

- `title`: nome della detections
- `id`: identificativo univoco
- `description`: spiegazione del comportamento da catturare
- `logsource`: sorgente dei log
- `detection`: condizioni logiche per il match
- `falsepositives`: scenari comuni che possono generare falsi positivi
- `level`: severità della regola

## Best practice

1. Mantenere regole piccole e specifiche.
2. Usare alias e campi normalizzati dove possibile.
3. Documentare chiaramente il contesto operativo.
4. Testare regole su dataset reali prima del deploy.
5. Aggiornare costantemente le whitelist e i tuning.

## Esempio mentale

Un attacco che sfrutta un comando PowerShell sospetto può essere rappresentato con una regola Sigma che cerca:

- esecuzione di `powershell.exe`
- parametri anomali
- connessioni outbound a host esterni
- pattern di download o decoding di payload

## Conclusione

Il valore di Sigma non è solo nella portabilità, ma anche nella capacità di costruire un framework di detections più leggibile e condivisibile tra team di sicurezza.
