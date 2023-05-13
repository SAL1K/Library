Installation/Configuration
------------------------------------------------
libmyodbc8a.so - Unicode
libmyodbc8a.so - ANSI

``` conf
cd /usr/src

wget https://dev.mysql.com/get/Downloads/Connector-ODBC/8.0/mysql-connector-odbc-8.0.26-linux-glibc2.12-x86-64bit.tar.gz

tar -xvf mysql-connector-odbc-8.0.26-linux-glibc2.12-x86-64bit.tar.gz

cd mysql-connector-odbc-8.0.26-linux-glibc2.12-x86-64bit/lib/

cp libmyodbc8w.so /usr/lib/x86_64-linux-gnu/odbc/
```

/etc/odbcinst.ini (Configure MySQL Driver)
------------------------------------------------
``` conf
[MySQL]
Description = ODBC for MySQL
Driver = /usr/lib/x86_64-linux-gnu/odbc/libmyodbc8w.so
FileUsage = 1
```

/etc/odbc.ini (Connection Via TPC)
------------------------------------------------
``` conf
[vmdb]
Description = MySQL connection to 'vmdb' database
Driver      = MySQL
Database    = vmdb
Server      = 127.0.0.1
Port        = 3306
User        = vm_user_db
Password    = 4[}qm?Yt^06Dj,*h
Option      = 3
```
/etc/odbc.ini (Connection Via Unix Socket)
------------------------------------------------
``` conf
[vmdb]
Description = MySQL connection to 'vmdb' database
Driver      = MySQL
Database    = vmdb
User        = vm_user_db
Password    = 4[}qm?Yt^06Dj,*h
Socket      = /var/run/mysqld2/mysqld2.sock
Option      = 3

[RBT]
Description = MySQL connection to 'RBT' database
Driver      = MySQL
Database    = RBT
User        = rbt_user_db
Password    = 8dgES6w0rOKLEZk9
Socket      = /var/run/mysqld/mysqld.sock
Option      = 3

[DIVR]
Description = MySQL connection to 'DIVR' database
Driver      = MySQL
Database    = DIVR
Server      = localhost
User        = divr_user_db
Password    = 9#_078]i25v@S@y9
Socket      = /var/lib/mysql/mysql.sock
```

``` bash
isql -v vmdb (Check connection via vmdb connector)
+---------------------------------------+
| Connected!                            |
|                                       |
| sql-statement                         |
| help [tablename]                      |
| quit                                  |
|                                       |
+---------------------------------------+
SQL>

SQL> select now();
+--------------------+
| now()              |
+--------------------+
| 2020-10-14 10:33:07|
+--------------------+
SQLRowCount returns 1
1 rows fetched
```

/etc/asterisk/res_odbc.conf
-------------------------------------
``` conf
[vmdb]
enabled=>yes
dsn=>vmdb
username=>vm_user_db
password=>4[}qm?Yt^06Dj,*h
pre-connect=>yes
max_connections=>300
```
/etc/asterisk/cdr_adaptive_odbc.conf
-------------------------------------
``` conf
;[CDR_calls]
;connection=vmdb
;table=CDR_calls
;usegmtime=no
;alias start => calldate
```
/etc/asterisk/cdr.conf
-------------------------------------
``` conf
[general]
enable=yes
unanswered=yes
congestion=yes
batch=yes
size=100
time=300
```

/etc/asterisk/func_odbc.conf
-------------------------------------
``` conf
[QUERY]
dsn       = FBII
readsql   = ${${ARG1}}
writesql  = ${${ARG1}}
mode      = multirow
synopsis  = run mysql query

asterisk -rx "module reload res_odbc.so"            (Только после согласования со мной)
asterisk -rx "module reload cdr_adaptive_odbc.so"   (Только после согласования со мной)
asterisk -rx "module reload func_odbc.so"       
asterisk -rx "module reload cdr.so"      (Только после согласования со мной)
asterisk -rx "cdr show status" 
```
#Unifun 