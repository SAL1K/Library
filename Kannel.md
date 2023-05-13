Это программа для создания смс-шлюза для отправки и получения сообщений.
Логи пишуться в BEARBOX_ACESS.log
пример смски для теста:
``` bash
curl "http://127.0.0.1:13101/cgi-bin/sendsms?username=smpp-test&password=smpp-test&from=AnrufInfo&to=436646997781&text=&priority=1&pid=64&alt-dcs=1&mclass=2&mwi=4&dlr-mask=27&dlr-url="
```
``` bash
curl "http://127.0.0.1:13000/status?password=kadmin"
```
Запуск контейнера для получения смс
``` bash
docker run -d -p2775:2775 komuw/smpp_server:v0.3
```
#Unifun 