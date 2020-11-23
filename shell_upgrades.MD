##### Python
```echo os.system("/bin/bash")```

```python -c 'import pty; pty.spawn("/bin/bash")'```


##### Perl
```perl -e 'exec "/bin/sh";'```

```exec "/bin/sh"```


##### Ruby
```exec "/bin/sh"```


##### LUA
```os.execute("/bin/sh")```


##### sh
```/bin/sh -i```


##### Vi
```:!bash```

```:set shell=/bin/bash:shell```


##### nmap
```!sh```


##### nano
```ctrl+r ctrl+x /bin/bash```


##### stty (fixed)
*In reverse shell:*

```python -c 'import pty;pty.spawn("/bin/bash")'```

*ctrl+z (to background)*

*In base OS:*

```stty raw -echo```

```reset```

```export SHELL=bash```

```export TERM=xterm-256color```

```stty rows <num> columns <cols>```


##### expect
*cat sh.exp*

```#!/usr/bin/expect```

```spawn sh```

```interact```

