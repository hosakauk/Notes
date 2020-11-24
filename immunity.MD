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




