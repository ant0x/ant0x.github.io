---
layout: single
title: "Come strutturare detections SIEM con Sigma"
date: 2026-06-24 12:00:00 +0200
categories: [soc, detections]
tags: [sigma, siem, detection-engineering]
author: "Antonio Baldi"
summary: "Una guida pratica per organizzare detections riconoscibili, portabili e facili da mantenere."
author_profile: true
toc: true
toc_sticky: true
read_time: true
image: /assets/images/sigma-detection-engineering.jpg
---

## Perché Sigma è importante

Sigma è diventato uno standard cruciale per descrivere regole di rilevamento in modo indipendente dal motore di sicurezza utilizzato. Il vantaggio principale è la possibilità di scrivere una regola una volta e poi riusarla su diversi SIEM, EDR o piattaforme di log management (Splunk, Microsoft Sentinel, Google Chronicle, Elasticsearch, etc.).

In questo articolo esploreremo come strutturare regole Sigma professionali, seguendo best practice adottate dai team SOC più efficienti.

## Struttura di una regola Sigma

Una regola Sigma è normalmente composta da:

```yaml
title: "Suspicious PowerShell Execution from C2 Domain"
id: 12345678-1234-1234-1234-123456789012
status: experimental
description: |
  Detects PowerShell process execution with indicators of C2 communication.
  This rule identifies suspicious parent processes (cmd.exe, explorer.exe)
  launching PowerShell with encoded commands or network activity.
references:
  - https://attack.mitre.org/techniques/T1059/001/
author: "Antonio Baldi"
date: 2026-06-24
modified: 2026-06-24
logsource:
  product: windows
  service: sysmon
detection:
  selection:
    EventID: 1
    Image|endswith: '\powershell.exe'
    ParentImage|endswith:
      - '\cmd.exe'
      - '\explorer.exe'
    CommandLine|contains:
      - '-nop'
      - '-enc'
      - 'FromBase64'
  filter:
    User|contains:
      - 'SYSTEM'
      - 'Administrator'
  condition: selection and not filter
falsepositives:
  - System administrators using encoded PowerShell commands for legitimate automation
  - IT scripts using PowerShell for system administration
level: high
```

## Best practice per regole Sigma professionali

### 1. **Specificity vs. Coverage**

Trovare il giusto equilibrio è cruciale. Una regola troppo specifica cattura solo il malware specifico ma genera troppi falsi negativi. Una troppo generica genera troppi falsi positivi e paralizza l'analyst.

**Esempio di regola troppo generica:**
```yaml
detection:
  keywords:
    - 'cmd.exe'
  condition: keywords
```

Questo cattura TUTTO ciò che contiene cmd.exe — milioni di eventi al giorno inutili.

**Esempio migliore:**
```yaml
detection:
  selection:
    Image|endswith: '\cmd.exe'
    CommandLine|contains:
      - 'whoami'
      - 'ipconfig'
      - 'tasklist'
  filter:
    ParentImage|endswith:
      - '\explorer.exe'  # filtri i launcher standard
  condition: selection and not filter
```

### 2. **Naming e metadata**

Nomi descrittivi e metadata completo aiutano il team SOC a capire immediatamente:

```yaml
title: "[CRITICAL] Lateral Movement via PsExec"
id: 3f2e4d5c-6789-1234-5678-9abcdef01234
status: stable  # experimental, test, stable, deprecated
description: |
  Detects lateral movement attempts using PsExec or similar tools.
  This technique is commonly used by attackers to move laterally within
  a network after initial compromise.
references:
  - https://attack.mitre.org/techniques/T1021/002/
  - https://attack.mitre.org/techniques/T1021/006/
author: "SOC Team"
date: 2026-06-24
modified: 2026-06-24
tags:
  - attack.lateral_movement
  - attack.t1021
```

### 3. **Field normalization**

Usa i campi normalizzati di Sigma per massima portabilità:

```yaml
logsource:
  product: windows
  service: sysmon        # Per processi
  # OR
  service: security      # Per event log di Windows
  # OR
  service: zeek          # Per network traffic
```

### 4. **Timely updates**

Le regole vanno aggiornate costantemente man mano che i threat actor cambiano tattica:

```yaml
modified: 2026-06-24    # Aggiorna SEMPRE questa data quando modifichi
status: stable          # Cambia da 'experimental' solo dopo testing
```

## Organizzazione in un team SOC

### Repository structure

```
sigma-rules/
├── detection-engineering/
│   ├── initial_access/
│   ├── lateral_movement/
│   ├── persistence/
│   └── exfiltration/
├── threat_feeds/
│   ├── apt_groups/
│   └── malware_families/
├── custom_detections/
├── tests/
└── README.md
```

### CI/CD e validation

Usa `sigma-cli` o `pySigma` per validare regole:

```bash
# Validate syntax
sigma check detection-engineering/**/*.yml

# Convert to Splunk
sigma convert -t splunk detection-engineering/**/*.yml > detections.spl

# Convert to Sentinel
sigma convert -t microsoft-sentinel detection-engineering/**/*.yml
```

## Metriche di efficacia

Traccia queste metriche per ogni regola:

- **True Positive Rate (TPR)**: % di alert che sono reali incidenti
- **False Positive Rate (FPR)**: % di alert che sono falsi positivi
- **Detection Latency**: Tempo medio da infezione a rilevamento
- **MTTR** (Mean Time To Response): Tempo medio di risposta dell'analyst

**Obiettivo:**
- TPR > 70%
- FPR < 5%
- Detections > 5 per settimana

## Conclusione

Sigma non è solo uno standard tecnico, è un framework per pensare in modo strutturato alle detections. Le regole ben scritte diventano il foundation della sicurezza operativa del tuo team.

Inizia con poche regole stabili, misura le metriche, itera. La qualità vince sulla quantità.

## Riferimenti

- [Sigma Documentation](https://sigma.readthedocs.io/)
- [MITRE ATT&CK](https://attack.mitre.org/)
- [pySigma GitHub](https://github.com/SigmaHQ/pySigma)
