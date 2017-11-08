# apache

## configure ports

* configure /etc/apache2/ports.conf
```
listen 80
>> listen 8080

then go to: /etc/apache2/site-enabled/000-default.conf
change first line:
<VirtualHost *: 8080>

now restart
sudo service apache2 restart
```


## problem solving

* apache2ctl configtest
to check the error

* check version:

`apachectl -v`

* check port conficted:

`sudo netstat -ltnp | grep ':80'`

https://bocoup.com/blog/apache-could-not-bind-address-to-port-make_sock
