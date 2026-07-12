# Data Sources

## Overview

Effective detection engineering depends on high-quality telemetry. The detections within this repository rely on commonly available enterprise log sources that are frequently ingested into Splunk deployments.

Different organizations may use different logging configurations; therefore, each detection specifies the minimum required data sources needed for reliable operation.

---

# Primary Data Sources

## Windows Security Event Logs

Provides authentication, account management, privilege changes, and process auditing events.

Common Event IDs include:

- 4624 — Successful Logon
- 4625 — Failed Logon
- 4672 — Special Privileges Assigned
- 4688 — Process Creation
- 4697 — Service Installation
- 4720 — User Created
- 4728 — Group Membership Added
- 4732 — Local Group Membership Added

---

## Sysmon

Microsoft Sysinternals Sysmon provides enhanced endpoint visibility beyond standard Windows logging.

Useful Event IDs include:

| Event ID  | Description        |
|-----------|--------------------|
| 1         | Process Creation   |
| 3         | Network Connection |
| 7         | Image Loaded       |
| 8         | CreateRemoteThread |
| 10        | Process Access     |
| 11        | File Creation      |
| 12-14     | Registry Events    |
| 22        | DNS Query          |

Sysmon significantly improves detection fidelity for process execution and attacker behavior.

---

## PowerShell Operational Logs

Location:

Applications and Services Logs

→ Microsoft

→ Windows

→ PowerShell

→ Operational

Provides visibility into:

- PowerShell execution
- Encoded commands
- Script blocks
- Module loading
- Remote PowerShell activity

---

## Windows Defender Logs

Useful for:

- Malware detections
- Antivirus configuration changes
- Security feature modifications
- Defender service status

---

## Firewall Logs

Provide visibility into:

- Allowed connections
- Blocked connections
- Suspicious outbound communication
- Port scanning activity

---

## DNS Logs

Useful for detecting:

- DNS tunneling
- Command and Control
- Beaconing
- Suspicious domain lookups

---

## Proxy / Web Logs

Useful for:

- Download cradles
- Malicious URLs
- Cloud storage uploads
- Data exfiltration

---

## VPN Logs

Useful for:

- Remote access monitoring
- Geographic anomalies
- Authentication failures
- Impossible travel

---

## Endpoint Detection & Response (EDR)

Examples include:

- Microsoft Defender for Endpoint
- CrowdStrike Falcon
- SentinelOne
- Carbon Black

EDR telemetry enhances process execution, behavioral detections, and investigation workflows.

---

# Logging Recommendations

For best detection coverage, organizations should enable:

- Process Creation Logging (4688)
- Command Line Auditing
- PowerShell Logging
- Script Block Logging
- Module Logging
- Sysmon
- DNS Logging
- Firewall Logging
- Authentication Auditing

---

# Splunk Common Index Examples

These detections assume logs may exist in indexes such as:

```
index=windows
index=sysmon
index=wineventlog
index=security
index=edr
```

Index names vary between environments and should be adjusted accordingly.
