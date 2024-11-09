# Часть 1
1) В директории text_processing создать файл kern.log с содержимым
```
Nov  6 08:15:40 hostname kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  6 08:15:40 hostname kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  6 08:15:40 hostname kernel: [    0.000000] Initializing cgroup subsys cpuacct
Nov  6 08:15:40 hostname kernel: [    0.000000] Linux version 5.4.0-42-generic (buildd@lgw01-amd64) (gcc version 9.3.0 (Ubuntu 9.3.0-17ubuntu1~20.04)) #46-Ubuntu SMP Wed Oct 14 10:36:50 UTC 2020
Nov  6 08:15:40 hostname kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-42-generic root=UUID=12345678-1234-1234-1234-123456789abc ro quiet splash
Nov  6 08:15:40 hostname kernel: [    0.000000] KERNEL supported cpus:
Nov  6 08:15:40 hostname kernel: [    0.000000]   Intel GenuineIntel
Nov  6 08:15:40 hostname kernel: [    0.000000]   AMD AuthenticAMD
Nov  6 08:15:40 hostname kernel: [    0.000000]   Hygon HygonGenuine
Nov  6 08:15:40 hostname kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x001
Nov  6 08:15:40 hostname kernel: [    0.001234] x86/fpu: xstate_offset[2]:    576, xstate_size:   2048
Nov  6 08:15:40 hostname kernel: [    0.001234] CPU0 microcode updated early to revision <revision_number>, date = <date>
Nov  6 08:15:40 hostname kernel: [    1.234567] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.LPC], AE_NOT_FOUND (20200428/psargs-330)
Nov  6 08:15:40 hostname kernel: [    1.234567] ACPI Error: Aborting method \_SB.PCI0.LPC due to previous error (AE_NOT_FOUND) (20200428/psparse-529)
```
2) В файле kern.log найти строки, содержащие Error и вывести имя хоста и само сообщение

<img width="852" alt="image" src="https://github.com/user-attachments/assets/e43d8765-3009-4540-b394-c71b09b98f5b">

3) В директории text_processing создать файл python.log с содержимым
```
2024-11-09 08:00:01,123 - myapp - INFO - The application is running.
2024-11-09 08:00:01,456 - myapp - DEBUG - Configuration initialization...
2024-11-09 08:00:01,789 - myapp - INFO - Database connection...
2024-11-09 08:00:02,012 - myapp - WARNING - Database is not responding, retry after 5 seconds.
2024-11-09 08:00:07,345 - myapp - ERROR - Failed to connect to the database: Timeout expired.
2024-11-09 08:00:07,678 - myapp - INFO - Shutdown of the application.
```
4) Из файла python.log вывести все записи, содержащие ERROR и вывести время и сообщение об ошибке
5) В директории text_processing создать файл searchd.log с содержимым
```
2024-11-09 08:00:01: [INFO] Sphinx 3.0.3 started
2024-11-09 08:00:01: [INFO] listening on 127.0.0.1:9306
2024-11-09 08:00:01: [INFO] listening on 127.0.0.1:9312
2024-11-09 08:00:01: [INFO] using config file '/home/user/sphinxdata/sphinx.conf'
2024-11-09 08:00:02: [DEBUG] starting indexer process
2024-11-09 08:00:02: [INFO] indexing index 'my_index'
2024-11-09 08:00:02: [INFO] collected 5000 documents, 1.2 MB
2024-11-09 08:00:02: [INFO] sorted 0.5 Mhits, 100.0% done
2024-11-09 08:00:02: [INFO] total indexed documents: 5000
2024-11-09 08:00:02: [INFO] total time spent indexing: 2.3 sec
2024-11-09 08:00:03: [WARNING] failed to open pid_file '/home/user/sphinxdata/searchd.pid'
2024-11-09 08:00:04: [ERROR] unable to connect to MySQL server at 'localhost': Access denied for user 'root'@'localhost' (using password: YES)
2024-11-09 08:00:05: [INFO] searchd stopped
```
6) В файле searchd.log найти записи, содержащие listening и вывести хост с портом
7) В директории text_processing создать файл rabbitmq.log с содержимым
```
2024-11-09 08:00:01.123 [info] <0.1234.0> Starting RabbitMQ 3.9.0 on Erlang 24.0
2024-11-09 08:00:01.456 [info] <0.1234.0> Server startup complete
2024-11-09 08:00:02.789 [info] <0.1235.0> Supervisor 'rabbit@localhost' started
2024-11-09 08:00:03.012 [warning] <0.1236.0> Connection failed: TCP connection to 127.0.0.1:5672 refused
2024-11-09 08:00:04.345 [error] <0.1237.0> Failed to open file /var/lib/rabbitmq/mnesia/rabbit@localhost/queues/queue1: No such file or directory
2024-11-09 08:00:05.678 [info] <0.1238.0> New client connection from 192.168.1.10:54321
2024-11-09 08:00:06.901 [info] <0.1239.0> Message published to exchange 'my_exchange'
2024-11-09 08:00:07.234 [critical] <0.1240.0> Node rabbit@localhost is shutting down
```
8) В файле rabbitmq.log найти записи critical и error
9) Получить из вывода команды free -h размер доступной памяти (available)
10) Получить из вывода команды lscpu количество ядер (CPU(s))
# Часть 2
1) Создать группы developers, designers, managers и admins
2) Создать пользователей jdoe, asmith, mjackson, kchen, rgarcia
3) Добавить пользователей
- mjackson в группу admins
- jdoe, kchen, rgarcia в группу developers
- asmith - в группу designers
4) Вывести из файла /etc/passwd только имена созданных пользователей
5) Вывести из файла /etc/group названия и состав добавленных групп
6) Задать пользователям пароли
7) Добавить пользователя asmith в группу managers
8) С помощью команды id получить информацию о пользователе asmith и вывести его первичную группу
9) Выполнить команду ```sudo getent shadow``` и из ее вывода получить имена добавленных в п2 пользователей и хеши их паролей
   В домашней директории создать директорию magento
10) В директории magento создать директории media, code и styles
11) В директории code создать файл index.php с содержимым
```
<?php
phpinfo();
?>
```
12) В директории styles создать файл main.css с содержимым
```
h1 {
    color: #333; /* Цвет текста */
    text-align: center; /* Выравнивание по центру */
}
```
13) В директории magento создать файл index.html с содержимым
```
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>E-commerce page</title>
    <link rel="stylesheet" href="styles.css"> <!-- Подключаем CSS -->
</head>
<body>
    <header>
        <h1>Welcome!</h1>
        <h2>e-commerce site</h2>
    </header>
```
14) Сделать владельцем файла index.html пользователя mjackson, а группой владельцев - группу developers
15) Сделать владельцем файла styles/main.css пользователя asmith, а группой владельцев - группу designers
16) Сделать владельцем файла code/index.php пользователя rgarcia, а группой владельцев - группу admins
# Часть 3
1) Выполнить команду
```
top &> /dev/null &
```
2) С помощью ps найти процесс top
3) В директории /proc найти каталог, который соответствует найденному выше процессу top
4) Убить процесс top
