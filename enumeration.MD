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

