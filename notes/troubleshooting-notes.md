# Troubleshooting Notes

## Issue 1

Alternate Data Stream not created.

### Cause

Incorrect stream syntax.

### Resolution

Use:

```powershell
Set-Content C:\ADSLab\Payroll.txt:SecretNotes.txt "Hidden Data"
```

---

## Issue 2

PowerShell returned only :$DATA.

### Cause

Hidden stream was not successfully created.

### Resolution

Recreate the ADS and verify using:

```powershell
Get-Item C:\ADSLab\Payroll.txt -Stream *
```

---

## Issue 3

Cannot read hidden stream.

### Cause

Incorrect stream name.

### Resolution

List available streams first:

```powershell
Get-Item C:\ADSLab\Payroll.txt -Stream *
```

Then use:

```powershell
Get-Content C:\ADSLab\Payroll.txt -Stream SecretNotes.txt
```

---

## Issue 4

dir /r does not display ADS.

### Cause

Incorrect directory or stream was removed.

### Resolution

Verify the correct folder:

```cmd
dir /r C:\ADSLab
```

---

## Issue 5

Remove-Item failed.

### Cause

Incorrect stream name.

### Resolution

List streams first and remove the correct stream:

```powershell
Remove-Item C:\ADSLab\Payroll.txt -Stream SecretNotes.txt
```

---

## Issue 6

File Explorer does not show hidden data.

### Cause

Alternate Data Streams are not visible in File Explorer.

### Resolution

Use PowerShell or Command Prompt to inspect NTFS streams.
