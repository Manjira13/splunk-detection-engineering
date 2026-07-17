
# Exfiltration

## Overview

Exfiltration techniques are used by adversaries to transfer collected data outside the organization's environment. Common methods include cloud storage services, FTP, DNS tunneling, encrypted web traffic, and large outbound file transfers.

Detecting exfiltration is critical to minimizing data loss and reducing the impact of security incidents.

This document contains the planned exfiltration detections maintained within this repository.

---

# Detection Coverage

| # | Detection | Status |
|---|-----------|--------|
| 1 | FTP Upload | Planned |
| 2 | DNS Tunneling | Planned |
| 3 | Cloud Storage Upload | Planned |
| 4 | Large Outbound Transfers | Planned |
| 5 | Data Compression Before Transfer | Planned |

---

# Detection Development Methodology

Each detection follows the repository's standardized detection engineering workflow.

---

# Future Improvements

- Network behavior analytics
- Proxy log integration
- DLP correlation
- Detection validation
