#### comments

| syntax | type |
|:---:|:---:|
|```--comment```|*oracle, microsoft, postgresql*|
|```-- comment```|*mysql*|
|```/*comment*/```|*microsoft, postgresql, mysql*|

-----


#### string concatenation

| syntax | type |
|:---:|:---:|
|```'foo'\|\|'bar'```|*oracle, postgresql*|
|```'foo'+'bar'```|*microsoft*|
|```'foo' 'bar'```|*mysql*|
|```CONCAT('foo','bar')```|*mysql*|

-----


#### version

| syntax | type |
|:---:|:---:|
|```SELECT version FROM v$instance```|*oracle*|
|```SELECT banner from v$instance```|*oracle*|
|```SELECT @@version```|*microsoft, mysql*|
|```SELECT version()```|*postgresql*|
