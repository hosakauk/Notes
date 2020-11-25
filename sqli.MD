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

-----


#### database contents

| syntax | type |
|:---:|:---:|
|```SELECT * FROM all_tables```|*oracle*|
|```SELECT * FROM all_tab_columns WHERE table_name = 'TABLE-NAME-HERE'```|*oracle*|
|```SELECT * FROM information_schema.tables```|*microsoft, postgresql, mysql*|
|```SELECT * FROM information_schema.columns WHERE table_name = 'TABLE-NAME-HERE'```|*microsoft, postgresql, mysql*|