#### show modules

```
!mona modules
```

-----


#### find "JMP ESP (\xFF\xE4)" in "some.dll"

```
!mona find -s "\xff\xe4" -m some.dll
```

-----


#### find offset after overflow

```
!mona findmsp
```

-----


#### specify bad characters for pointers (-cpb)

```
!mona jmp -r esp -cpb "\x00\x0A"
```

-----


#### convert assembly instructions to opcode

```
!mona assembly -s "pop eax#inc ebx#ret"
```

-----


#### find ROP gadgets

```
!mona rop -m *.dll -cp nonull
```

-----


#### set breakpoint on all imported functions in myapp.exe that contain "mem"

```
!mona bf -t ADD -f import -s *mem* -m myapp.exe
```

-----


#### set breakpoint on given address if the address is read

```
!mona bp -a 0x0012C431 -t READ
```

-----


#### set breakpoint on given address if the address is written to

```
!mona bp -a 0x0012C431 -t WRITE
```

-----


#### create bytearray appending bytes "\x00\x0a\x0d"

```
!mona bytearray -b '\x00\x0a\x0d'
```

-----


#### compare byte array to saved crash

```
!mona bytearray -b '\x00\x0a\x0d'
```

-----


#### dump all bytes from 0012F100 to 0012F200 to file c:\tmp\test.bin

```
!mona dump -s 0x0012F100 -e 0x0012F200 -f "c:\tmp\test.bin"
```

-----


#### find all locations where string "w00t" can be found

```
!mona find -type asc -s "w00t"
```

-----


#### find all executable locations that have a pointer to "JMP ECX"

```
!mona find -type instr -s "jmp ecx" -p2p -x X
```

-----


#### find all locations that have a pointer to any of the pointers in file "c:\temp\seh.txt"

```
!mona find -type file -s "c:\temp\seh.txt" -p2p -x *
```

-----


#### search for a PUSH (any register), followed (*not immediately) by POP EAX, followed (directly) by INC EAX, ending (*not immediately) with RETN

```
!mona findwild -s "push r32#*#pop eax#inc eax#*#retn"
```

-----


#### output file header

```
!mona header -f c:\temp\song.s3m
```

-----


#### help

```
!mona help findmsp
```

-----


#### pattern create

```
!mona pattern_create 5000
```

-----


#### pattern offset

```
!mona pattern_offset \x01\x02\x03\x04
```

-----


#### generate rop gadgets and automatically attempts to produce ROP chains using 4 particular modules, and list the stackpivots with a distance between 800 and 1200 bytes.

```
!mona rop -m "libglib,libatk,libgdk-win32,libgtk-win32" -distance 800,1200
```

-----


