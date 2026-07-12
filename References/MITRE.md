# MITRE ATT&CK Reference

## Overview

This repository aligns every detection with the MITRE ATT&CK® Enterprise Framework to provide standardized threat mapping and improve analyst understanding of adversary behavior.

Rather than focusing solely on individual attack tools or malware families, MITRE ATT&CK categorizes adversary actions into tactics and techniques based on observed real-world behavior. This enables consistent detection engineering, threat hunting, and incident response across different environments.

Each completed detection within this repository includes its corresponding ATT&CK tactic, technique, and technique identifier where applicable.

---

## Why MITRE ATT&CK?

Using the ATT&CK framework provides several advantages:

- Standardized detection documentation
- Consistent threat classification
- Easier detection gap analysis
- Improved SOC analyst workflows
- Better reporting to security teams
- Alignment with industry best practices

---

## Enterprise ATT&CK Tactics Covered

| Tactic                | Description                                               |
|-----------------------|-----------------------------------------------------------|
| Initial Access        | Techniques used to gain initial entry into an environment |
| Execution             | Methods used to execute malicious code                    |
| Persistence           | Techniques that maintain long-term access                 |
| Privilege Escalation  | Obtaining higher-level permissions                        |
| Defense Evasion       | Avoiding detection or bypassing security controls         |
| Credential Access     | Stealing or abusing credentials                           |
| Discovery             | Enumerating systems, users, or network information        |
| Lateral Movement      | Moving between hosts within an environment                |
| Collection            | Gathering data of interest                                |
| Exfiltration          | Transferring collected data outside the environment       |

---

## Detection Mapping

Each detection documents:

- ATT&CK Tactic
- ATT&CK Technique
- ATT&CK Technique ID
- Detection rationale

Example:

| Detection                    | Technique                   |
|------------------------------|-----------------------------|
| Encoded PowerShell Execution | T1059.001 – PowerShell      |
| Windows Defender Disabled    | T1562.001 – Impair Defenses |
| Scheduled Task Creation      | T1053.005 – Scheduled Task  |

---

## ATT&CK Coverage

This project focuses on enterprise Windows environments commonly monitored by Security Operations Centers (SOCs).

Future updates will expand coverage across:

- Linux
- Microsoft 365
- Azure
- AWS
- Microsoft Defender
- Sysmon
- EDR telemetry

---

## Official Resources

- MITRE ATT&CK Enterprise Matrix
- ATT&CK Navigator
- ATT&CK Data Sources
- ATT&CK Techniques
