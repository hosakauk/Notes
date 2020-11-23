###### python
```echo os.system("/bin/bash")```
```python -c 'import pty; pty.spawn("/bin/bash")'```
```Then: ctrl+z (to background), stty raw -echo, fg (enter)```

###### perl
```perl -e 'exec "/bin/sh";'```
```exec "/bin/sh"```

###### ruby
```exec "/bin/sh"```

###### lua
```os.execute("/bin/sh")```

###### sh
```/bin/sh -i```

