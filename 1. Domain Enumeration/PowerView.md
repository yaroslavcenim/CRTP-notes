**Domain:**
```powershell
Get-Domain
Get-Domain -Domain stark.local
Get-DomainSID
```

**Domain policy:**
```powershell
Get-DomainPolicyData
Get-DomainPolicyData -domain stark.local
```

**Users:**
```powershell
Get-DomainUser
Get-DomainUser -Identity student
Get-DomainUser -Identity student -Properties *
Get-DomainUser -Properties samaccountname, logonCount
Get-DomainUser -LDAPFilter "Description=*built*" | select name,Description
```

**Computers:**
```powershell
Get-DomainComputer | select name
Get-DomainComputer -OperatingSystem "*Server 2022*"
Get-DomainComputer -Ping
```

**Groups:**
```powershell
Get-DomainGroup | select name
Get-DomainGroup -UserName "student"
Get-DomainGroup -Domain stark.local
Get-DomainGroup *admin*
Get-DomainGroupMember -Identity "Domain Admins"
```

**Local groups:**
```powershell
Get-NetLocalGroup -ComputerName DC01
Get-NetLocalGroupMember -ComputerName DC01 -GroupName Administrators
```

**Logged users:**
```powershell
Get-NetLoggedon -ComputerName DC01
Get-LoggedonLocal -ComputerName DC01
Get-LastLoggedOn -ComputerName DC01
```

**Shares:**
```powershell
Invoke-ShareFinder -Verbose
Invoke-FileFinder -Verbose
Get-NetFileServer
```

**GPO:**
```powershell
Get-DomainGPO
Get-DomainGPO -ComputerIdentity DC01
Get-DomainGPOLocalGroup
Get-DomainGPOComputerLocalGroupMapping -ComputerIdentity DC01
Get-DomainGPOUserLocalGroupMapping -Identity student -Verbose
```

**OUs:**
```powershell
Get-DomainOU
Get-DomainGPO -Identity "{gplink}"
```

**ACLs:**

```powershell
Get-DomainObjectAcl -SamAccountName student -ResolveGUIDs
Get-DomainObjectAcl -SearchBase "LDAP://" -ResolveGUIDs -Verbose
Find-InterestingDomainAcl -ResolveGUIDs
Find-InterestingDomainAcl -ResolveGUIDs | ?{$_.IdentityReferenceName -match "studentX"}
Get-PathAcl -Path "\\stark.local\sysvol"
```

**Trusts:**
```powershell
Get-DomainTrust
Get-DomainTrust -Domain stark.local
```

**Forest:**
```powershell
Get-Forest
Get-Forest -Forest stark.local
Get-ForestDomain
Get-ForestDomain -Forest stark.local
Get-ForestGlobalCatalog
Get-ForestGlobalCatalog -Forest stark.local
Get-ForestTrust
Get-ForestTrust -Forest stark.local
```

**Local admin access:**
```powershell
Find-LocalAdminAccess -Verbose
```

**Find sessions — PowerView (admin):**
```powershell
Find-DomainUserLocation -Verbose
Find-DomainUserLocation -UserGroupIdentity "RDPUsers"
```

**Find sessions — SessionHunter:**
```powershell
Invoke-SessionHunter -FailSafe
Invoke-SessionHunter -NoPortScan -Targets C:\servers.txt
```