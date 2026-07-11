# Splunk Detection Engineering

> **Project Status:** In Progress

A practical collection of **Splunk detection engineering use cases** designed to simulate real-world Security Operations Center (SOC) detection development. This repository focuses on creating production-style Splunk SPL detections mapped to the **MITRE ATT&CK Framework**, complete with investigation workflows, false-positive analysis, severity ratings, and response recommendations.

Unlike repositories that simply list search queries, this project documents the reasoning behind each detection and demonstrates the thought process involved in developing actionable alerts for SOC analysts.

---

# Project Objectives

This project aims to:

- Develop practical security detections using Splunk SPL.
- Map detections to the MITRE ATT&CK Enterprise Framework.
- Improve threat visibility across the attack lifecycle.
- Document investigation procedures for SOC analysts.
- Reduce false positives through detection tuning.
- Build reusable detection engineering documentation.
- Simulate enterprise SOC detection development practices.

---

# Skills Demonstrated

- Detection Engineering
- Splunk SPL
- Threat Detection
- SOC Alert Triage
- Blue Team Operations
- Security Monitoring
- Windows Event Analysis
- Threat Hunting
- Incident Investigation
- MITRE ATT&CK Mapping
- Detection Tuning
- Security Documentation

---

# Detection Methodology

Each detection in this repository follows a standardized documentation format similar to what would be maintained by an internal Detection Engineering or Blue Team.

Every detection includes:

- Overview
- Objective
- MITRE ATT&CK Mapping
- Detection Severity
- Data Sources
- Required Logs
- Splunk SPL Query
- Detection Logic
- Investigation Workflow
- Expected False Positives
- Detection Tuning Recommendations
- Response Guidance
- References

---

# Detection Categories

The repository is organized according to the MITRE ATT&CK Enterprise tactics.

## Initial Access

Detect techniques used by attackers to gain an initial foothold.

**Planned detections**

- Multiple Failed Logins
- Successful Login After Multiple Failures
- Suspicious RDP Authentication
- Suspicious SMB Authentication
- VPN Login from New Location

---

## Execution

Detect malicious command execution and script abuse.

**Planned detections**

- Encoded PowerShell Execution 
- Office Spawning PowerShell
- Office Spawning CMD
- Rundll32 Execution
- Regsvr32 Execution
- MSHTA Execution
- WMIC Process Execution
- PowerShell Download Cradle
- Script Host Execution
- Suspicious CMD Execution

---

## Persistence

Detect mechanisms used by attackers to maintain access.

**Planned detections**

- Scheduled Task Creation
- Registry Run Key Modification
- Startup Folder Persistence
- New Windows Service
- WMI Event Subscription
- New Local User Creation

---

## Privilege Escalation

Detect attempts to gain elevated privileges.

**Planned detections**

- Local Administrator Added
- Domain Admin Group Modification
- Privileged Group Membership Changes
- Token Manipulation Indicators

---

## Defense Evasion

Detect attempts to disable or bypass security controls.

**Planned detections**

- Windows Defender Disabled
- Security Log Cleared
- Firewall Disabled
- Event Logging Disabled
- Suspicious AV Service Stopped

---

## Credential Access

Detect attempts to steal or access credentials.

**Planned detections**

- LSASS Memory Access
- Mimikatz Detection
- SAM Database Access
- Credential Dumping Activity
- Browser Credential Theft

---

## Discovery

Detect reconnaissance activity performed after initial compromise.

**Planned detections**

- whoami
- hostname
- net user
- net group
- ipconfig
- netstat
- arp
- nltest
- systeminfo

---

## Lateral Movement

Detect attacker movement between systems.

**Planned detections**

- PsExec Execution
- Remote Service Creation
- WMI Execution
- SMB Admin Share Access
- Remote Scheduled Tasks

---

## Collection

Detect collection of sensitive information before exfiltration.

**Planned detections**

- Archive Creation
- Mass File Compression
- Clipboard Collection
- Browser Data Collection

---

## Exfiltration

Detect movement of data outside the environment.

**Planned detections**

- Large Outbound Data Transfers
- FTP Upload Activity
- Suspicious Cloud Storage Upload
- DNS Tunneling
- Data Compression Before Transfer

---

# Repository Structure

```text
splunk-detection-engineering/
│
├── README.md
│
├── detections/
│   ├── Initial_Access.md
│   ├── Execution.md
│   ├── Persistence.md
│   ├── Privilege_Escalation.md
│   ├── Defense_Evasion.md
│   ├── Credential_Access.md
│   ├── Discovery.md
│   ├── Lateral_Movement.md
│   ├── Collection.md
│   └── Exfiltration.md
│
└── references/
    ├── MITRE.md
    └── Data_Sources.md
```

---

# Detection Workflow

Each detection follows a structured engineering workflow.

```text
Threat Technique
        │
        ▼
Log Source Identification
        │
        ▼
Splunk Data Collection
        │
        ▼
Detection Logic Development
        │
        ▼
SPL Query Creation
        │
        ▼
Validation & Tuning
        │
        ▼
False Positive Analysis
        │
        ▼
SOC Investigation Workflow
        │
        ▼
Response Recommendations
```

---

# Current Progress

| Category | Status |
|-----------|:------:|
| Repository Structure |  Complete |
| Documentation Framework |  Complete |
| MITRE Mapping |  In Progress |
| Data Sources |  In Progress |
| Execution Detections |  In Progress |
| Remaining Detection Categories |  Planned |

---

# Roadmap

## Phase 1

- Repository setup
- Detection documentation framework
- MITRE ATT&CK mapping
- Data source documentation
- Initial execution detections

---

## Phase 2

- Initial Access detections
- Persistence detections
- Privilege Escalation detections
- Defense Evasion detections

---

## Phase 3

- Credential Access detections
- Discovery detections
- Lateral Movement detections
- Collection detections
- Exfiltration detections

---

## Phase 4

- Detection tuning
- False positive optimization
- Detection coverage improvements
- Additional enterprise use cases

---

# References

The repository includes additional documentation covering:

- MITRE ATT&CK Framework
- Windows Log Sources
- Sysmon Event IDs
- Splunk Data Sources
- Detection Engineering Best Practices

Documentation can be found in the **references/** directory.

---

# Future Improvements

Planned enhancements include:

- Additional enterprise detection use cases
- Detection tuning examples
- Risk scoring methodology
- Detection testing procedures
- Sigma rule mappings
- Detection coverage matrix
- ATT&CK Navigator mapping
- Detection maturity tracking

---

# Disclaimer

This repository is intended for **educational and defensive cybersecurity purposes only**. All detection logic is designed to improve threat detection capabilities and support Security Operations Center (SOC) workflows. No offensive or unauthorized activities are encouraged or supported.

---

# License

This project is released under the MIT License.
