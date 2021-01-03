## web
-----
#### allowed http methods

```nmap --script=http-methods x.x.x.x```

```nmap --script http-methods --script-args http-methods.url-path='/website' x.x.x.x```

-----


#### vhost bruteforce

```gobuster vhost -u example.com -w some_wordlist.txt```

```gobuster -u example.com -w some_wordlist.txt vhost```

-----


#### interesting web files

```gobuster dir -u mytarget.com -w path/to/my/awesome/wordlist.txt -e -t 100 -x php,txt,html,htm```

-----


#### find images

```gobuster dir -u mytarget.com -w path/to/my/awesome/wordlist.txt -e -t 100 -x jpg,jpeg,png,gif,ico```

-----


#### skip SSL verification

```gobuster dir -u mytarget.com -w path/to/my/awesome/wordlist.txt -k```

-----


#### bypass basic auth

```gobuster dir -u mytarget.com -w path/to/my/awesome/wordlist.txt -U BasicAuthUser -P BasicAuthPass```

-----

## snmp
-----
#### snmp v1 query

```snmpwalk -v1 -c [Community string] [IP address of the host] [OID of the system information MIB]```

-----

#### snmp v2 query

```snmpwalk -v2c -c -c [Community string] [IP address of host] [OID of system information MIB]```

-----

#### snmp v3 query auth no encryption

```snmpwalk -v3 -l authNoPriv -u [User name] -a MD5 -A [User password] [IP address of host] [OID of system information MIB]```

-----

#### snmp v3 query auth and encryption

```snmpwalk -v3 -l authPriv -u [User name] -a MD5 -A [User password] -x DES -X [DES password] [IP address of host] [OID of system information MIB]```

-----

#### snmp v3 no auth no encryption

```snmpwalk -v3 -l noAuthNoPriv -u [User name] [IP address of the host] [OID of the system information MIB]```

-----
