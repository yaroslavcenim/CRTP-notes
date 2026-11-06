**Domain:**
```powershell
Get-ADDomain
Get-ADDomain -Identity stark.local
(Get-ADDomain).DomainSID
```

**Users:**
```powershell
Get-ADUser -Filter * -Properties *
Get-ADUser -Identity student -Properties *
Get-ADUser -Filter * -Properties * | select -First 1 | Get-Member -MemberType *Property | select Name
```

**Computers:**
```powershell
Get-ADcomputer -Filter * | select Name
Get-ADcomputer -Filter * -Properties *
```

**Groups:**
```powershell
Get-ADGroup -Filter * | select Name
Get-ADGroup -Filter * -Properties *
Get-ADGroup -Filter 'Name -like "*admin*"' | select Name
Get-ADGroupMember -Identity "Domain Admins" -Recursive
Get-ADPrincipalGroupMembership -Identity student

```
