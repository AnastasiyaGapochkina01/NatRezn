# Часть 1
1) В домашней директории создать директорию temp-files
2) В temp-files создать файлы test.txt main.go server.py и директорию copies
3) Скопировать файлы test.txt main.go server.py в директорию copies
4) Переименовать файл copies/test.txt в tests.py
5) Создать директорию python и скопировать в нее файлы server.py и tests.py
6) Создать директорию go и переместить в нее файл main.go
7) Из директории temp-files удалить все файлы.
Директории copies, python и go должны остаться вместе с содержимым, те при выполнении ls и tree в директории temp-files выывод должен быть такой:
```
~/temp-files » ls
copies go     python

~/temp-files » tree -a
.
├── copies
│   ├── main.go
│   ├── server.py
│   └── tests.py
├── go
│   └── main.go
└── python
    ├── server.py
    └── tests.py

4 directories, 6 files
```
8) В домашней директории создать директорию temp-backups
9) Скопировать все содержимое директории temp-files в temp-backups
10) В директории temp-backups создать файл bkp-credentials
11) Переименовать файл bkp-credentials в .env
12) Удалить директорию temp-files
# Часть 2
1) Выполнить команду
```
sleep 1000 &
```
2) Найти процесс sleep, какой у него id?
3) Убить процесс sleep
4) С помощью systemctl проверить статус nginx
5) Найти все процессы nginx, убрав из вывода процесс grep
6) С помощью systemctl остановить nginx
7) С помощью ps посмотреть, остались ли процессы nginx
8) С помощью systemctl запустить nginx
9) С помощью ps посмотреть, появились ли процессы nginx
10) Попробовать убить один из worker процессов nginx. Посмотреть с помощью ps запустится ли новый worker на замену убитому
