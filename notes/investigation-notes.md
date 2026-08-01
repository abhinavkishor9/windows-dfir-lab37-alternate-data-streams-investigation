# Investigation Notes

## Lab Summary

This investigation focused on detecting and analyzing NTFS Alternate Data Streams (ADS) using native Windows tools and PowerShell.

The investigation reconstructed hidden file activity by creating an Alternate Data Stream, validating its existence using multiple tools, comparing visible and hidden content, and confirming successful removal.

---

## Analyst Methodology

1. Create investigation workspace.
2. Create a sample file.
3. Add visible file content.
4. Create an Alternate Data Stream.
5. Store hidden information.
6. Compare visible and hidden contents.
7. Detect ADS using PowerShell.
8. Detect ADS using Command Prompt.
9. Remove the hidden stream.
10. Validate cleanup.
11. Document findings.

---

## Investigation Scenario

A normal text file was created to simulate a legitimate document.

Hidden information was then stored inside an Alternate Data Stream attached to that file.

The investigation aimed to determine:

- Whether hidden data existed.
- Whether the hidden data altered the original file.
- How ADS could be detected.
- How hidden content could be recovered.
- Whether the stream could be safely removed.

---

## Evidence Collected

### Evidence 1 – Investigation Workspace

Collected:

- ADSLab folder

Finding:

Established investigation workspace.

---

### Evidence 2 – Sample File

Collected:

- Payroll.txt

Finding:

Created baseline evidence.

---

### Evidence 3 – Alternate Data Stream

Collected:

- SecretNotes.txt ADS

Finding:

Successfully attached hidden stream to Payroll.txt.

---

### Evidence 4 – Visible vs Hidden Content

Collected:

- Default file contents
- Hidden ADS contents

Finding:

Visible file remained unchanged while hidden data was successfully recovered.

---

### Evidence 5 – PowerShell Detection

Command Used

```powershell
Get-Item C:\ADSLab\Payroll.txt -Stream *
```

Finding:

Detected both the default stream and the hidden Alternate Data Stream.

---

### Evidence 6 – Command Prompt Detection

Command Used

```cmd
dir /r C:\ADSLab
```

Finding:

Confirmed ADS existence through NTFS stream enumeration.

---

### Evidence 7 – ADS Removal

Command Used

```powershell
Remove-Item C:\ADSLab\Payroll.txt -Stream SecretNotes.txt
```

Finding:

Hidden stream removed successfully while preserving the original file.

---

## DFIR Analysis

The investigation demonstrated how NTFS Alternate Data Streams can conceal information without modifying a file's visible contents.

By correlating PowerShell enumeration, Command Prompt output, and file content validation, the investigation successfully identified, examined, and removed the hidden stream.

---

## MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|----|
| Defense Evasion | Hide Artifacts: NTFS Alternate Data Streams | T1564.004 |
| Discovery | File and Directory Discovery | T1083 |

---

## Analyst Observations

- ADS allows hidden information to exist independently of visible file contents.
- File Explorer does not display Alternate Data Streams.
- PowerShell provides reliable ADS enumeration.
- Command Prompt (`dir /r`) independently validates hidden streams.
- Removing an ADS does not affect the visible file contents.

---

## Conclusion

The investigation demonstrated how NTFS Alternate Data Streams can be detected, analyzed, and removed using native Windows utilities while emphasizing structured evidence collection, artifact validation, and forensic documentation.
