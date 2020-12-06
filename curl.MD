#### POST Form Data

```curl -X POST -F 'username=admin' -F 'password=default' http://www.example.com/form.php```

-----


#### POST JSON Data

```curl -X POST -H 'Content-Type: application/json' -d '{"username":"admin","password":"default"}' http://www.example.com/login.php```

*Note: -d or --data is the same as --data-ascii (this will also strip line breaks), sending binary data requires --data-binary and to URL encode the value of a form field use --data-urlencode*

-----

#### MOVE file

```curl -X MOVE --header Destination:http://example.com/something.jpg http://example.com/something.php```

-----


#### PUT file

```curl -d "example data" -X PUT http://example.com/test.html```

```curl -T localfile http://example.com/file```

```cat shell.php | curl -d "$(>/dev/stdin)" -X PUT http://example.com/shell.php```

-----


#### POST JSON data file

```curl -X POST -d "@file.json" http://www.example.com/form-api.php```

-----


#### POST application/x-www-form-urlencoded

```curl -X POST -d "param1=value1&param2=value2" http://www.example.com/form.php```

```curl -X POST -d "param1=value1&param2=value2" -H "Content-Type: application/x-www-form-urlencoded" http://www.example.com/form.php```

-----


#### POST application/x-www-form-urlencoded with file

```curl -X POST -d "@file.txt" http:///www.example.com/form.php```

-----


#### Get Numerical Sequence

```curl http://www.example.com/?page=[0-10]```

-----


#### Get Alphabetical Sequence

```curl http://www.example.com/?page=[a-z]```

-----

