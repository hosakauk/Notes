#### find directories owned by "apache"
-----
```find / . -type d -user apache 2>&1 | grep -v "Permission denied"```


#### find files owned by "apache"
-----
```find / . -type f -user apache 2>&1 | grep -v "Permission denied"```


#### grep recursive
-----
```grep -r somestring /somedir/somewhere```


#### find sh files
-----
```find / . -name "*.sh"```


#### find writable files
-----
```find / . -perm -o+w```


#### find files newer than 120 minutes
-----
```find / . -type f -mmin -120```


#### users and groups info
-----
```groups (primary listed first)```

```groups <username>```

```id <username>```

```getent sudo <username>```


#### suid binaries in /bin
-----
```find /bin -perm -4000```


#### suid and setgid bit
-----
```find / -xdev -user root \( -perm -4000 -o -perm -2000 \)```


#### owned by root world writable
-----
```find / . -uid 0 -perm a+w```


#### owned by root world writable (no /dev)
-----
```find / . -xdev -user root -perm -a+w```



