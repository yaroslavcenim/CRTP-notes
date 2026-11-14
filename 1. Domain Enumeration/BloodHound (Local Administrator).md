**Collection data to BloodHound:**
```powershell
# Use PowerShell
Import-Module SharpHound.ps1
Invoke-BloodHound -CollectionMethod All

# Use .exe
SharpHound.exe
```

**Stealth collection data to BloodHound:**
```powershell
# Use PowerShell
Import-Module SharpHound.ps1
Invoke-BloodHound -Stealth # Avoid detections like MDI: -ExcludeDCs

# Use .exe
SharpHound.exe --stealth
```
