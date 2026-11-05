**PowerView:** https://github.com/PowerShellMafia/PowerSploit/tree/master/Recon
**Invoke-SessionHunter:** https://github.com/Leo4j/Invoke-SessionHunter

**Domain:**
	Get-Domain
	Get-Domain -Domain stark.local
	Get-DomainSID

**Domain policy:**
	Get-DomainPolicyData
	Get-DomainPolicyData -domain stark.local

**Users:**
	Get-DomainUser
	Get-DomainUser -Identity student
	Get-DomainUser -Identiry student -Properties *
	Get-DomainUser -Properties samaccountname, logonCount
	Get-DomainUser -LDAPFilter "Description=\*built\*" | select name,Description

**Computers:**
	Get-DomainComputer | select name
	Get-DomainComputer -OperatingSystem "\*Server 2022\*"
	Get-DomainComputer -Ping

**Groups:**
	Get-DomainGroup | select name
	Get-DomainGroup -UserName "student"
	Get-DomainGroup -Domain stark.local
	Get-DomainGroup \*admin\*
	Get-DomainGroupMember -Identity "Domain Admins"

**Local groups:**
	Get-NetLocalGroup -ComputerName DC01
	Get-NetLocalGroupMember -ComputerName DC01 -GroupName Administrators

**Logged users:**
	Get-NetLoggedon -ComputerName DC01
	Get-LoggedonLocal -ComputerName DC01
	Get-LastLoggedOn -ComputerName DC01

**Shares:**
	Invoke-ShareFinder -Verbose
	Invoke-FileFinder -Verbose
	Get-NetFileServer

**GPO:**
	Get-DomainGPO
	Get-DomainGPO -ComputerIdentity DC01
	Get-DomainGPOLocalGroup
		Get-DomainGPOComputerLocalGroupMapping -ComputerIdentity DC01
		Get-DomainGPOUserLocalGroupMapping -Identity student -Verbose

**OUs:**
	Get-DomainOU
		Get-DomainGPO -Identity "{gplink}"

**ACLs:**
	Get-DomainObjectAcl -SamAccountName student -ResolveGUIDs
	Get-DomainObjectAcl -SearchBase "LDAP://" -ResolveGUIDs -Verbose
	Find-InterestingDomainAcl -ResolveGUIDs
	Find-InterestingDomainAcl -ResolveGUIDs | ?{$\_.IdentityReferenceName -match "studentX"}
	Get-PathAcl -Path "\\\stark.local\sysvol"
	
**Trusts:**
	Get-DomainTrust
	Get-DomainTrust -Domain stark.local

**Forest:**
	Get-Forest
	Get-Forest -Forest stark.local
	Get-ForestDomain
	Get-ForestDomain -Forest stark.local
	Get-ForestGlobalCatalog
	Get-ForestGlobalCatalog -Forest stark.local
	Get-ForestTrust
	Get-ForestTrust -Forest stark.local

**Local Admin Access:**
	Find-LocalAdminAccess -Verbose

**Find Sessions:**
	*PowerView(admin):*
		Find-DomainUserLocation -Verbose
		Find-DomainUserLocation -UserGroupIdentity "RDPUsers"
	*SessionHunter:*
		Invoke-SessionHunter -FailSafe
		Invoke-SessionHunter -NoPortScan -Targets C:\servers.txt