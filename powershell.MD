#### auth as user alice and add user bob
-----
```
$username = 'alice'
$password = 'alicepassword'
$pass = ConvertTo-SecureString -AsPlainText $password -Force
$cred = New-Object System.Management.Automation.PSCredential -ArgumentList $username,$pass
Invoke-Command -Credential $cred -ScriptBlock {net localgroup Administrators bob /add}
```


#### bypass execution policy
-----
```
powershell -ExecutionPolicy ByPass -File C:\example.ps1
```


#### start shell as user alice
-----
```
$username = 'alice'
$password = 'alicepassword'
$pass = ConvertTo-SecureString -AsPlainText $password -Force
$cred = New-Object System.Management.Automation.PSCredential -ArgumentList $username,$pass
Start-Process cmd.exe -Credential $cred
```


#### convert file to base64 (UTF16 little endian (windows format))
-----
```
cat somefile.ps1 | iconv -t UTF-16LE | base64 -w0 
powershell -enc <pastebase64here>
```