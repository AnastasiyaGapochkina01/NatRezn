# Часть 1
1) Повторить материалы
- https://rus-linux.net/MyLDP/BOOKS/Linux_Foundations/6/ch06.html
- https://www.ispmanager.ru/news/struktura-fajlovoj-sistemy-linux
2) Повторно выполнить задание https://github.com/AnastasiyaGapochkina01/NatRezn/blob/main/home-work-2.md
# Часть 2
1) Написать bash скрипт, который получает информацию о свободной памяти на машине и делает запись в файл meminfo.log формата
```
date time hostname [INFO] Mem usage is 145Mib
```
то есть
```
2025-01-25 11:17 server-1 [INFO] Mem usage is 145Mib
```
2) Написать bash скрипт, который выводит в файл user.list список пользователей в формате
```
username - id: $ID
```
то есть
```
root - id: 0
avahi - id: 1
```
3) Написать bash скрипт, который выводит в файл hostinfo.out имя машины, версию операционной системы, размер диска, смонтированного в корень, ip-адрес.
например
```
server_name: server-1 os: Debian 11 disk_size: 40G ip: 10.0.1.15
```
