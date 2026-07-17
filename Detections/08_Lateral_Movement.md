
# Lateral Movement

## Overview

Lateral Movement techniques enable adversaries to move from one compromised system to another within an environment. Successful lateral movement often precedes privilege escalation, credential theft, or ransomware deployment.

Detecting remote execution and administrative protocols is essential for limiting attacker spread.

This document contains the planned lateral movement detections maintained within this repository.

---

# Detection Coverage

| # | Detection | Status |
|---|-----------|--------|
| 1 | PsExec | Planned |
| 2 | Remote Service Creation | Planned |
| 3 | WMI Execution | Planned |
| 4 | SMB Admin Shares | Planned |
| 5 | Remote Scheduled Tasks | Planned |

---

# Detection Development Methodology

Each detection follows the repository's standardized detection engineering workflow.

---

# Future Improvements

- Multi-host correlation
- RBA implementation
- Atomic Red Team validation
- Threat hunting guidance
