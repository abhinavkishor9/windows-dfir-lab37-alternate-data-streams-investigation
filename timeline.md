# Investigation Timeline

| Time | Activity | Evidence |
|------|----------|----------|
| 06:37 | Created ADSLab workspace | PowerShell |
| 06:39 | Created Payroll.txt | PowerShell |
| 06:41 | Added visible file content | Get-Content |
| 06:42 | Created Alternate Data Stream | Set-Content |
| 06:43 | Added additional hidden data | Add-Content |
| 06:44 | Compared visible and hidden contents | Get-Content |
| 06:45 | Enumerated ADS using PowerShell | Get-Item -Stream * |
| 06:46 | Validated ADS using Command Prompt | dir /r |
| 06:47 | Removed Alternate Data Stream | Remove-Item -Stream |
| 06:48 | Confirmed cleanup | Get-Item -Stream * |

---

# Investigation Flow

Investigation Started

↓

Created Investigation Workspace

↓

Created Sample File

↓

Added Visible Content

↓

Created Alternate Data Stream

↓

Stored Hidden Information

↓

Compared Visible vs Hidden Contents

↓

Detected ADS Using PowerShell

↓

Validated ADS Using Command Prompt

↓

Removed Hidden Stream

↓

Confirmed Cleanup

↓

Investigation Completed

---

# Summary

The investigation demonstrated how NTFS Alternate Data Streams can conceal information without changing a file's visible contents. Using native Windows tools, the hidden stream was successfully created, detected through both PowerShell and Command Prompt, examined independently of the primary file, and safely removed. The lab highlighted how ADS can be abused for data concealment and how DFIR analysts can identify and validate these artifacts during forensic investigations.
