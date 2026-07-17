# Execution

## Overview

The Execution tactic consists of techniques that adversaries use to run malicious code on a compromised system. Detecting execution activity is critical because it often represents the first observable stage after initial access.

Many execution techniques rely on legitimate Windows binaries (LOLBins), scripting engines, or administrative utilities to evade detection. High-quality detections combine process creation telemetry, command-line auditing, PowerShell logging, and behavioral analysis to distinguish legitimate administration from malicious execution.

This document contains the planned execution detections maintained within this repository.

---

# Detection Coverage

| # | Detection | Status |
|---|-----------|--------|
| 1 | Encoded PowerShell Execution | ✅ Complete |
| 2 | Office Spawning PowerShell | Planned |
| 3 | Office Spawning CMD | Planned |
| 4 | Rundll32 Execution | Planned |
| 5 | Regsvr32 Execution | Planned |
| 6 | MSHTA Execution | Planned |
| 7 | WMIC Execution | Planned |
| 8 | PowerShell Download Cradle | Planned |
| 9 | Script Host Execution | Planned |
| 10 | Suspicious CMD Execution | Planned |

---

# Detection 1: Encoded PowerShell Execution

## Overview

PowerShell is a legitimate Windows administration framework frequently abused by adversaries due to its flexibility, native availability, and ability to execute scripts entirely in memory.

Attackers commonly use the `-EncodedCommand` (`-enc`) parameter to conceal malicious commands by encoding them in Base64. This technique helps evade simple keyword-based detections and reduces the visibility of malicious payloads during execution.

Monitoring for encoded PowerShell commands provides an effective high-confidence detection for suspicious activity while maintaining manageable false-positive rates in most enterprise environments.

---

## Objective

Identify PowerShell processes launched using encoded command-line arguments that may indicate malicious script execution, payload staging, or post-exploitation activity.

---

## MITRE ATT&CK Mapping

| Field | Value |
|--------|-------|
| Tactic | Execution |
| Technique | Command and Scripting Interpreter: PowerShell |
| Technique ID | T1059.001 |

---

## Severity

**High**

Reasoning:

- Frequently associated with malware execution.
- Common in ransomware campaigns.
- Widely observed during post-exploitation.
- Often used by penetration testing tools and offensive frameworks.

---

## Data Sources

- Windows Security Logs
- Sysmon Event ID 1
- PowerShell Operational Logs

---

## Required Logs

Minimum recommended telemetry:

- Sysmon Process Creation (Event ID 1)
- Windows Event ID 4688 (Process Creation)
- PowerShell Operational Logs
- Command-Line Auditing Enabled

---

## Splunk SPL Query

```spl
index=windows
(EventCode=4688 OR EventCode=1)
(Image="*powershell.exe" OR NewProcessName="*powershell.exe")
(CommandLine="*-enc *"
OR CommandLine="*-EncodedCommand *"
OR CommandLine="* encodedcommand *")
| table _time Computer User Image CommandLine ParentImage
| sort - _time
```

---

## Detection Logic

This detection searches process creation events for PowerShell executions containing encoded command parameters.

The detection focuses on:

- -enc
- -EncodedCommand
- EncodedCommand

Process metadata including parent process, user account, host, and execution time is returned to support rapid triage.

---

## Investigation Workflow

### Step 1 — Validate the Process

- Confirm PowerShell executable path.
- Verify the executing user.
- Review the parent process.
- Determine whether execution originated from an Office application, browser, script host, or scheduled task.

---

### Step 2 — Review Command Line

Determine:

- Was the command Base64 encoded?
- Is the encoded payload unusually long?
- Does it contain download or execution functionality?

---

### Step 3 — Decode the Payload

Safely decode the Base64 content within an isolated analysis environment.

Review for:

- Download cradles
- Invoke-WebRequest
- IEX (Invoke-Expression)
- Reflection
- AMSI bypasses
- Credential theft
- Persistence creation

---

### Step 4 — Investigate Host Activity

Review surrounding activity including:

- Network connections
- Child processes
- Registry modifications
- Scheduled task creation
- New services
- File creation

---

### Step 5 — Determine Business Justification

Confirm whether:

- System administrators executed the command
- Automation tools generated the activity
- Endpoint management software initiated PowerShell

If no legitimate explanation exists, escalate for incident response.

---

## Expected Results

Legitimate examples may include:

- Enterprise management scripts
- Configuration management platforms
- Administrative automation

Suspicious examples include:

- Malware loaders
- Cobalt Strike
- Empire
- Metasploit
- Ransomware execution
- Living-off-the-land attacks

---

## False Positives

Potential false positives include:

- SCCM deployments
- Intune management scripts
- PowerShell automation
- Configuration management tools
- Backup software
- Enterprise monitoring agents

---

## Tuning Recommendations

Reduce false positives by:

- Allowlisting trusted administrative accounts
- Excluding approved automation servers
- Monitoring parent-child process relationships
- Correlating with PowerShell Operational Logs
- Prioritizing unsigned or unexpected PowerShell executions
- Combining with network or EDR telemetry for higher confidence

---

## Response Guidance

If malicious activity is suspected:

1. Isolate the affected endpoint.
2. Preserve relevant logs and forensic evidence.
3. Decode and analyze the PowerShell payload in a secure environment.
4. Review additional activity performed by the process.
5. Identify persistence mechanisms or lateral movement.
6. Reset compromised credentials if required.
7. Hunt across the environment for similar executions.
8. Update detection logic with new indicators where appropriate.

---

## References

- MITRE ATT&CK T1059.001
- Microsoft PowerShell Logging Documentation
- Splunk Security Content
- Microsoft Sysmon Documentation

---

# Detection Development Methodology

Each detection in this repository follows a standardized engineering process:

1. Identify a commonly abused ATT&CK technique.
2. Determine the required telemetry.
3. Develop and validate the SPL query.
4. Document investigation procedures.
5. Identify potential false positives.
6. Recommend tuning strategies.
7. Define analyst response guidance.
8. Map the detection to MITRE ATT&CK.

This methodology emphasizes repeatability, consistency, and operational value for Security Operations Centers.

---

# Future Improvements

Planned enhancements include:

- Risk-Based Alerting (RBA) examples
- Splunk Enterprise Security correlation searches
- Detection testing using Atomic Red Team
- Sample attack datasets
- SPL optimization techniques
- Detection coverage metrics
- Detection validation notes
- Detection version history
