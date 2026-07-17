
# Credential Access

## Overview

Credential Access techniques focus on stealing, extracting, or abusing authentication material such as passwords, password hashes, Kerberos tickets, and browser-stored credentials.

Detecting credential access activity is a high priority because compromised credentials frequently enable privilege escalation and lateral movement.

This document contains the planned credential access detections maintained within this repository.

---

# Detection Coverage

| # | Detection | Status |
|---|-----------|--------|
| 1 | LSASS Memory Access | Planned |
| 2 | Mimikatz Detection | Planned |
| 3 | SAM Database Access | Planned |
| 4 | Credential Dumping | Planned |
| 5 | Browser Credential Theft | Planned |

---

# Detection Development Methodology

Each detection follows the repository's standardized detection engineering workflow.

---

# Future Improvements

- Memory analysis integration
- Sigma mappings
- Atomic Red Team validation
- Detection performance improvements
