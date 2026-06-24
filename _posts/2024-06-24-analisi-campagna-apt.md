---
layout: single
title: "Analisi campagna APT"
date: 2024-06-24 10:00:00 +0200
categories: [cti, analisi]
tags: [APT, threat-intel, italian]
author: "Antonio Baldi"
summary: "Analisi sintetica di una campagna APT osservata su infrastrutture europee."
author_profile: true
toc: true
toc_sticky: true
read_time: true
---

## Sommario

Questo articolo fornisce una panoramica di una campagna APT osservata nel Q2 2024 che ha preso di mira organizzazioni del settore energetico in Europa. L'analisi è di carattere educativo e fornisce indicatori, TTPs e raccomandazioni di mitigazione.

## Osservazioni principali

- Tattiche principali: spear-phishing con allegati LNK/ISO, uso di loader personalizzati e C2 via HTTPS.
- Obiettivi: raccolta di credenziali, movimento laterale e esfiltrazione di documenti sensibili.
- Probabile gruppo: comportamento coerente con APTxx (asimmetria nelle infrastrutture C2, uso di certificati legittimi).

## Tecniche e procedure (TTP)

- Initial Access: Phishing mirato (T1566.001) tramite email con allegati malevoli.
- Execution: File LNK che eseguono un loader che poi carica un payload in memoria.
- Persistence: Modifiche al registro (Run keys) e scheduled tasks.
- Privilege Escalation: Exploit locali sconosciuti o abuso di servizi amministrativi.
- Lateral Movement: Uso di PsExec e WMIC per esecuzione remota.
- Command and Control: Canale HTTPS con domini dinamici e certificati válidi.

## Indicatori di compromissione (IOC)

Esempi osservati (fittizi per l'articolo):

- Domini C2:
  - secure-update-service[.]com
  - patch-server-eu[.]net

- Indirizzi IP:
  - 45.77.12.34
  - 185.62.99.101

- Hash dei sample (SHA256):
  - 3b1f2c9e4a5b6c8d9e0f1a2b3c4d5e6f7a8b9c0d1e2f3a4b5c6d7e8f9a0b1c2

## Raccomandazioni di mitigazione

1. Rafforzare la formazione anti-phishing per gli utenti con simulazioni mirate.
2. Applicare policy di blocco per allegati potenzialmente pericolosi (.lnk, .iso, .scr) a livello di mail-gateway.
3. Abilitare EDR con capacità di detection basate su comportamento (in-memory execution, anomalie di PowerShell/WMIC).
4. Implementare MFA su tutti gli accessi privilegiati e monitorare i login sospetti da nuove località.
5. Segmentazione della rete e controllo delle credenziali amministrative.

## Conclusioni

La campagna mostra una combinazione di tecniche mature e infrastrutture resilienti; la difesa efficace richiede controllo delle email, monitoraggio continuo e pratiche di risposta agli incidenti aggiornate.

## Riferimenti

- MITRE ATT&CK: https://attack.mitre.org
- Guide pratiche su difesa dalle minacce APT: vendor whitepaper e report CTI pubblici.

<!-- Se vuoi includere immagini, aggiungile in assets/images e referenziale qui -->
