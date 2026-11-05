```powershell
# PSSession
New-PSSession -ComputerName DC01
Enter-PSSession

# Execute commands or scriptblocks
Invoke-Command -Scriptblock {Get-Process} -ComputerName (Get-Content servers.txt)

# Execute scripts from files
Invoke-Command -FilePath C:\Get-PassHashes.ps1 -ComputerName (Get-Content servers.txt)

# Execute locally loaded function
Invoke-Command -ScriptBlock ${function:Get-Domain} -ComputerName DC01

# Execute "Stateful" commands using Invoke-Command
	$Sess = New-PSSession -Computername DC01
	Invoke-Command -Session $Sess -ScriptBlock {\$Proc = Get-Process}
	Invoke-Command -Session $Sess -ScriptBlock {\$Proc.Name}
```

**Winrs.exe:**
```cmd
winrs -r:DC01 cmd
winrs -remote:DC01 -u:DC01\administrator -p:pass
```
