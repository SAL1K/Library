По дефолту стоит RADIUS или syslog.

|        Имя         | Назначение                                                                        | Юзабельность                                                                      |
|:------------------:|:--------------------------------------------------------------------------------- |:--------------------------------------------------------------------------------- |
| cdr_adaptive_odbc  | Позволяет записывать CDR через ODBC с возможностью добавления настраиваемых полей | <font style="color:#24e1ab">Полезный</font>                                       |
|      cdr_csv       | Записывает CDR на диск как файл значений, разделенных запятыми                    | <font style="color:#f4d41d">Годный</font>                                         |
|     cdr_custom     | Записывает CDR в CSV-файл, но позволяет добавлять настраивыемые поля              | <font style="color:#24e1ab">Полезный</font>                                       |
|    cdr_manager     | Выводит CDR в AMI                                                                 | <font style="color:#24e1ab">Полезный</font>                                       |
|      cdr_odbc      | Записывает CDR через структуру ODBC                                               | <font style="color:#f4d41d">Годный</font>                                         |
|     cdr_pgsql      | Записывает CDR в PostgreSQL                                                       | <font style="color:#24e1ab">Полезный</font>                                       |
|     cdr_radius     | Записывает CDR в RADIUS                                                           | <font style="color:#f4d41d">Годный</font> — не поддерживает пользовательские поля |
| cdr_sqlite3_custom | Записывает CDR в базу данных SQLite3 с пользовательскими полями                   | <font style="color:#24e1ab">Полезный</font>                                       |
|     cdr_syslog     | Записывает CDR в syslog                                                           | <font style="color:#24e1ab">Полезный</font>                                       |
|      cdr_tds       | Записывает CDR в Microsoft SQL и Sybase                                           | <font style="color:#f4d41d">Годный</font> - требуется старая версия libtds        |
#Unifun 