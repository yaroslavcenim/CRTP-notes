**Run all checks:**
```powershell
# PowerUP
Invoke-AllChecks

# Privesc
Invoke-PrivEsc
```

**PowerUP(services)**
```powershell
# Unquoted path and space in name
Get-ServiceUnquoted -Verbose

# Modifiable File
Get-ModifiableServiceFile -Verbose

# Modifiable Service
Get-ModifiableService -Verbose
```
