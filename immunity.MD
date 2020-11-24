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





