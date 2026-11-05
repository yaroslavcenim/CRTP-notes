**Instruments:**
	**PowerUp:** https://github.com/PowerShellMafia/PowerSploit/tree/master/Privesc
	**Privesc:** https://github.com/enjoiz/Privesc
	**winPEAS:** https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS

**Run all checks from:**
	**PowerUP:**
		Invoke-AllChecks
	**Privesc:**
		Invoke-PrivEsc

**PowerUP(services)**
	**Unquoted path and space in name:**
		Get-ServiceUnquoted -Verbose
	**Modifiable File:**
		Get-ModifiableServiceFile -Verbose
	**Modifiable Service:**
		Get-ModifiableService -Verbose
