# windows-dfir-lab37-alternate-data-streams-investigation
## Overview

NTFS Alternate Data Streams (ADS) are a lesser-known feature of the Windows NTFS file system that allows additional hidden data to be attached to a file without changing its visible contents. While ADS has legitimate uses, attackers frequently abuse it to hide scripts, credentials, malware, or other data from casual inspection.

In this hands-on DFIR lab, a normal text file was created and hidden data was stored inside an Alternate Data Stream. Native Windows tools and PowerShell were then used to detect, inspect, compare, and remove the hidden stream while preserving the original file.

---

# Executive Summary

This investigation demonstrates how NTFS Alternate Data Streams can conceal data without affecting a file's visible contents. Using only built-in Windows utilities, hidden streams were created, detected, examined, and removed, illustrating how DFIR analysts can identify file concealment techniques during forensic investigations.

The workflow mirrors a common host-based forensic investigation involving evidence creation, artifact discovery, validation, and remediation.

---

# Investigation Objectives

- Understand NTFS Alternate Data Streams.
- Create a normal file.
- Store hidden information inside an ADS.
- Compare visible versus hidden file contents.
- Detect Alternate Data Streams using PowerShell.
- Detect ADS using Command Prompt.
- Remove the hidden stream.
- Validate successful cleanup.
- Document investigation findings.

---

# Skills Demonstrated

- NTFS File System Analysis
- Alternate Data Streams (ADS)
- Windows DFIR Methodology
- PowerShell Investigation
- Command Prompt Forensics
- Hidden Data Detection
- Host-Based Forensics
- Evidence Correlation
- Windows Artifact Analysis
- Incident Documentation

---

# Tools Used

- Windows 10
- Windows PowerShell
- Command Prompt
- File Explorer

---

# Lab Environment

| Component | Details |
|-----------|---------|
| Operating System | Windows 10 |
| Investigation Type | Host-Based DFIR |
| Analysis Method | Native Windows Tools |
| Primary Artifact | NTFS Alternate Data Streams |
| Shell | Windows PowerShell |
| Privileges | Administrator |

---

# Investigation Workflow

1. Create investigation workspace.
2. Create a sample file.
3. Add visible file content.
4. Create an Alternate Data Stream.
5. Store hidden information.
6. Compare visible and hidden contents.
7. Detect ADS using PowerShell.
8. Detect ADS using Command Prompt.
9. Remove the Alternate Data Stream.
10. Validate cleanup.
11. Document findings.

---

# MITRE ATT&CK Mapping

| Technique | Description |
|-----------|-------------|
| T1564.004 | Hide Artifacts: NTFS File Attributes / Alternate Data Streams |
| T1083 | File and Directory Discovery |
| T1005 | Data from Local System |
| T1070 | Indicator Removal on Host |

---

# Evidence Collected

- ADSLab workspace
- Payroll.txt sample file
- Hidden Alternate Data Stream
- PowerShell ADS enumeration
- Command Prompt ADS enumeration
- Hidden stream contents
- Stream removal evidence

---

# Evidence Correlation

The investigation correlated multiple evidence sources to validate the presence of hidden data:

- Visible file contents remained unchanged after the hidden stream was added.
- PowerShell successfully enumerated both the default data stream and the hidden ADS.
- Command Prompt (`dir /r`) confirmed the presence of the alternate stream.
- After removal, only the default data stream remained, confirming successful cleanup.

---

# Investigation Findings

The investigation confirmed that Alternate Data Streams allow hidden information to be attached to an NTFS file without altering its visible contents. Native Windows utilities were sufficient to identify, inspect, and remove the concealed stream, demonstrating an effective DFIR workflow for detecting hidden artifacts on Windows systems.

---

# Key Takeaway

Alternate Data Streams remain a common technique for hiding data on NTFS volumes. DFIR analysts should routinely inspect ADS during host investigations, as hidden streams may contain scripts, credentials, malware, or other evidence not visible through standard File Explorer views.
