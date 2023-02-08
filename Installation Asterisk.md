### OS: Ubuntu 20.04.3 LTS
Установка необходимых пакетов:
``` bash
apt-get install build-essential libxml2 libxml2-dev libmysqlclient-dev libhiredis-dev
```
-----------------------
### Install Bison 1.28
```bash
{
wget --no-check-certificate https://ftp.gnu.org/gnu/bison/bison-1.28.tar.gz
tar -xvf bison-1.28.tar.gz
cd bison-1.28
./configure --prefix=/usr/local/bison --with-libiconv-prefix=/usr/local/libiconv/
make
make install
ln -s /usr/local/bison/bin/bison /usr/bin/bison
ln -s /usr/local/bison/bin/yacc /usr/bin/yacc
}
```
----------------------------
### Install Kannel 1.4.5

``` bash
{
wget --no-check-certificate https://redmine.kannel.org/attachments/download/322/gateway-1.4.5.tar.gz
tar -xvf gateway-1.4.5.tar.gz
cd gateway-1.4.5/
./configure --prefix=/etc/kannel --with-mysql --with-redis --enable-start-stop-daemon 
make 
make install
mkdir /var/log/kannel
cd /etc/init.d/
Copy file kannel to directory on the server /etc/init.d/
chmod +x kannel
Copy file kannel.conf to directory on the server /etc/kannel
/etc/init.d/kannel start
}
```
#Unifun