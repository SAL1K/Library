Это программа для создания смс-шлюза для отправки и получения сообщений.
Логи пишуться в BEARBOX_ACESS.log
пример смски для теста:
``` bash
curl "http://127.0.0.1:13101/cgi-bin/sendsms?username=smpp-test&password=smpp-test&from=AnrufInfo&to=436646997781&text=&priority=1&pid=64&alt-dcs=1&mclass=2&mwi=4&dlr-mask=27"
```
