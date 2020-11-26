#### auth as user alice and add user bob

```
$username = 'alice'
$password = 'alicepassword'
$pass = ConvertTo-SecureString -AsPlainText $password -Force
$cred = New-Object System.Management.Automation.PSCredential -ArgumentList $username,$pass
Invoke-Command -Credential $cred -ScriptBlock {net localgroup Administrators bob /add}
```

-----


#### bypass execution policy

```
powershell -ExecutionPolicy ByPass -File C:\example.ps1
```

-----


#### start shell as user alice

```
$username = 'alice'
$password = 'alicepassword'
$pass = ConvertTo-SecureString -AsPlainText $password -Force
$cred = New-Object System.Management.Automation.PSCredential -ArgumentList $username,$pass
Start-Process cmd.exe -Credential $cred
```

-----


#### convert file to base64 (UTF16 little endian (windows format))

```
cat somefile.ps1 | iconv -t UTF-16LE | base64 -w0 
powershell -enc <pastebase64here>
```

-----


#### copy files and folders (local to remote pc)

```
copy-item E:\WindowsImageBackup\exchange -destination \\server1\Backups\Exchange -recurse -verbose
```

-----


#### list all accounts with no password expire

```
get-aduser -filter * -properties Name, PasswordNeverExpires | where {$_.passwordNeverExpires -eq "true" } | Select-Object DistinguishedName,Name,Enabled
```

-----


#### get all computers in active directory

```
Get-AdComputer -filter *
```

-----


#### get all computers in active directory by name

```
Get-ADComputer -filter * | select name
```

-----


#### get all disabled users

```
Search-ADAccount -AccountDisabled | select name
```

-----


#### get all locked users in active directory

```
Search-ADAccount -LockedOut
```

-----


#### get all security groups in active directory

```
Get-ADGroup -filter *
```

-----


#### get all windows 10 computers in active directory

```
Get-ADComputer -filter {OperatingSystem -Like '*Windows 10*'} -property * | select name, operatingsystem
```

-----


#### get count by operating system

```
Get-ADComputer -Filter "name -like '*'" -Properties operatingSystem | group -Property operatingSystem | Select Name,Count
```

-----


#### get number of computers in a domain

```
Get-ADComputer -filter * | measure
```

-----


#### get users in security group "HR"

```
Get-ADGroupMember -identity “HR”
```

-----


#### read file contents

```
Get-Content -Path "c:\boot.ini"
```

```
$MyVar = Get-Content C:\temp\MyFile.txt
invoke-item c:\temp\MyFile.txt
```

-----


#### remote shell session

```
Enter-PSSession -ComputerName
```

-----


#### restart remote computer(s)

```
Restart-Computer -ComputerName "Server01", "Server02", "localhost"
```

-----


#### search for string in files (recursive)

```
Get-ChildItem -recurse | Select-String -pattern "dummy" | group path | select name
```

-----


#### unlock user in active directory

```
Unlock-ADAccount –Identity john.smith
```

-----


#### search for windows 7 machines in active directory (specify forest) and output to file

```
Get-ADComputer -Filter {OperatingSystem -like '*Windows 7*'} -SearchBase "ou=OrgUnit,dc=domain,dc=local" | Select-Object Name,DNSHostName,OperatingSystemVersion,Enabled | Out-File C:\temp\win7_list.txt
```

-----


#### get user details from active directory

```
Get-ADUser -Identity some.person -Server SERV.DOMAIN.WHEREVER ` -Properties AccountLockoutTime,LastBadPasswordAttempt,BadPwdCount,LockedOut,BadPasswordTime,LastLogonDate
```

```
Get-ADUser -Identity some.person -Server SERV.DOMAIN.WHEREVER ` -Properties *
```

```
Get-NetUser -Username student1
```

```
Get-NetUser | select -ExpandProperty samaccountname
```

-----


#### find shares on hosts in current domain

```
Invoke-ShareFinder -Verbose
```

```
Invoke-ShareFinder -ExcludeStandard -ExcludePrint -ExcludeIPC -Verbose
```

-----


#### get local administrators of remote computer

```
function get-localadmins{
 [cmdletbinding()]
 Param(
 [string]$computerName
 )
 $group = get-wmiobject win32_group -ComputerName $computerName -Filter "LocalAccount=True AND SID='S-1-5-32-544'"
 $query = "GroupComponent = `"Win32_Group.Domain='$($group.domain)'`,Name='$($group.name)'`""
 $list = Get-WmiObject win32_groupuser -ComputerName $computerName -Filter $query
 $list | %{$_.PartComponent} | % {$_.substring($_.lastindexof("Domain=") + 7).replace("`",Name=`"","\")}
}

$Workstation = Read-Host "Computer Name"
get-localadmins $Workstation
```

-----


#### change ownership of files in directory

```
$files = Get-ChildItem $PWD
foreach ($f in $files){
	TAKEOWN /F $f /A
	icacls $f /grant Administrators:F /t}
```

-----


#### get list of GPO in current domain

```
Get-NetGPO
Get-NetGPO -ComputerName DC01.enumme.local
Get-GPO -All (GroupPolicy module)
Get-GPResultantSetOfPolicy -ReportType Html -Path C:\Users\Administrator\report.html (Provides RSoP)
```

-----

