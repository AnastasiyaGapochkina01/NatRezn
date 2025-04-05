1) Перейти в директорию docker-data и находясь в ней запустить контейнер с именем nextcloud-local, с
- сопоставлением директории ./nextcloud-data на хосте с директорией /var/www/html в контейнере
- сопоставлением порта 8000 хоста с портом 80 контейнера
- image - nextcloud\
Все прошло успешно, если при обращении на публичный ip и порт 8000 показывается такое
<img width="854" alt="image" src="https://github.com/user-attachments/assets/29fb61d1-6996-4df2-8813-2cb3f496b2c0" />

2) В директории docker-data создать директорию python-src. В python-src создать файл hello.py с содержимым
```
#!/usr/bin/python
import socket
import os
import pwd
user_name = pwd.getpwuid(os.getuid())[0]
host_name = socket.gethostname()
print(f"Hello, {user_name} you inside in {host_name}")
```
3) Запустить контейнер с именем python-app, с
- сопоставлением файла python-src/hello.py на хосте с файлом /app/hello.py в контейнере
- image - python:3.12\
Зайти в контейнер python-app и выполнить ```python /app/hello.py```. Если вывод похож на ```Hello, root you inside in 1adc7f445dc9```, то все ок
4) В директории docker-data/php-data создать файл info.php с содержимым
```
<?php
echo "Версия ОС сервера: " . php_uname() . "\n";
echo "Тип ОС сервера: " . PHP_OS . "\n";

$serverIp = gethostbyname(gethostname());
echo "IP-адрес сервера: " . $serverIp . "\n";
?>
```
5) Запустить контейнер с именем php-cli, с
- сопоставлением директории php-data на хосте с директорией /app в контейнере
- image - php\
Зайти в контейнер php-cli и посмотреть содержимое директории /app. Должно быть
```
ls /app
index.php info.php 
```
Выполнить ```php /app/info.php``` в контейнере. Если вывод примерно такой
```
Версия ОС сервера: Linux 6b53817c4c3f 5.10.0-34-amd64 #1 SMP Debian 5.10.234-1 (2025-02-24) x86_64
Тип ОС сервера: Linux
IP-адрес сервера: 172.17.0.2
```
то все ОК
