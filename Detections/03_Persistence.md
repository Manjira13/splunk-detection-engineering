
# Persistence

## Overview

The Persistence tactic consists of techniques that adversaries use to maintain access to a compromised system after the initial intrusion. Persistence mechanisms enable attackers to survive system reboots, user logoffs, password changes, and other routine administrative actions.

Detecting persistence techniques is critical because they often indicate an attacker has successfully established a foothold within the environment. Effective detection relies on monitoring process creation, registry modifications, scheduled task activity, service creation, Windows Management Instrumentation (WMI), and user account changes.

This document contains the planned persistence detections maintained within this repository.

---

# Detection Coverage

| # | Detection | Status |
|---|-----------|--------|
| 1 | Scheduled Task Creation | Planned |
| 2 | Registry Run Keys | Planned |
| 3 | Startup Folder Persistence | Planned |
| 4 | Windows Service Creation | Planned |
| 5 | WMI Event Subscription | Planned |
| 6 | New Local User Creation | Planned |

---

# Detection Development Methodology

Each detection follows a standardized engineering process:

1. Identify the ATT&CK technique.
2. Determine required telemetry.
3. Develop and validate the SPL query.
4. Document investigation workflow.
5. Identify false positives.
6. Recommend tuning strategies.
7. Define analyst response guidance.
8. Map the detection to MITRE ATT&CK.

---

# Future Improvements

- Risk-Based Alerting (RBA)
- Atomic Red Team validation
- Splunk ES correlation searches
- Detection version history
- Detection testing notes
