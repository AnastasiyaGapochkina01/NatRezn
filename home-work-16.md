# Часть 0
Повторить предыдущую домашку
https://github.com/AnastasiyaGapochkina01/NatRezn/blob/main/home-work-15.md
# Часть 1
1) В домашней директории создать директорию text_processing
2) В директории text_processing создать файл apache_access.log с содержимым
```
192.168.1.1 - - [15/Jan/2025:10:00:00 +0300] "GET /index.html HTTP/1.1" 200 2326 "http://example.com" "Mozilla/5.0"
192.168.1.2 - - [15/Jan/2025:10:01:00 +0300] "POST /submit HTTP/1.1" 302 512 "http://lms.example.com" "Mozilla/5.0"
192.168.1.3 - - [15/Jan/2025:10:02:00 +0300] "GET /about.html HTTP/1.1" 200 2048 "http://admin.example.com" "Mozilla/5.0"
192.168.1.4 - - [15/Jan/2025:10:03:00 +0300] "GET /contact.html HTTP/1.1" 404 512 "http://admin.example.com" "Mozilla/5.0"
192.168.1.5 - - [15/Jan/2025:10:04:00 +0300] "POST /products.html HTTP/1.1" 200 3000 "http://lms.example.com" "Mozilla/5.0"
192.168.1.6 - - [15/Jan/2025:10:05:00 +0300] "GET /services.html HTTP/1.1" 200 1500 "http://example.com" "Mozilla/5.0"
192.168.1.7 - - [15/Jan/2025:10:06:00 +0300] "GET /index.html HTTP/1.1" 200 2326 "http://example.com" "Mozilla/5.0"
```

<img width="858" alt="image" src="https://github.com/user-attachments/assets/666148d6-869c-4dfd-86b4-6e7453e18757" />

3) В файле apache_access.log найти все строки, содержащие lms.example.com и вывести для них ip-адрес
4) В файле apache_access.log найти все строки, содержащие метод POST и вывести код ответа
5) В файле apache_access.log найти все строки, содержащие код ответа 404
6) В директории text_processing создать файл php-error.log с содержимым
```
[36.252.172.99] PHP Parse error:  syntax error, unexpected 'if' (T_IF) in /var/www/html/broken_script.php on line 68
[12-Jan-2025 08:08:01] [110.1.177.127] PHP Parse error:  syntax error, unexpected 'if' (T_IF) in /var/www/html/broken_script.php on line 60
[11-Jan-2025 13:45:01] [137.117.251.143] PHP Parse error:  syntax error, unexpected 'if' (T_IF) in /var/www/html/broken_script.php on line 11
[10.195.86.143] PHP Fatal error:  Uncaught Error: Call to undefined function nonexistent_function() in /var/www/html/functions.php:83
[96.187.17.230] PHP Fatal error:  Uncaught Error: Call to undefined function nonexistent_function() in /var/www/html/functions.php:48
[11-Jan-2025 17:10:01] [235.4.34.31] PHP Parse error:  syntax error, unexpected 'if' (T_IF) in /var/www/html/broken_script.php on line 65
[11-Jan-2025 10:57:01] [86.145.153.114] PHP Parse error:  syntax error, unexpected 'if' (T_IF) in /var/www/html/broken_script.php on line 97
[11-Jan-2025 22:55:01] [27.89.66.40] PHP Parse error:  syntax error, unexpected 'if' (T_IF) in /var/www/html/broken_script.php on line 73
[82.133.144.106] PHP Notice:  Undefined variable: undefined_var in /var/www/html/script.php on line 81
```
7) В файле php-error.log найти строки, содержащие Uncaught Error и вывести первый столбец
8) В файле php-error.log найти строки, содержащие Undefined variable и вывести в какой строке ошибка

<img width="806" alt="image" src="https://github.com/user-attachments/assets/b8d35408-570c-4d0c-adf4-eefa7f6071bd" />

# Часть 2
1) В директории text_processing создать файл long-long-file
2)  В директории text_processing создать файл create_file.sh с содержимым
 ```
#!/bin/bash
for i in {1..100}; do echo "$(hostname) $(date +%M:%S)" >> long-long-file; sleep 2; done &
```
3) Сделать файл create_file.sh исполняемым для всех
4) Выполнить команду ```./create_file.sh```
5) Найти в выводе команды ps процесс create_file.sh и вывести только его pid и comm
6) Посмотреть содержимое файла long-long-file
7) Убить процесс create_file.sh
8) Создать директорию temp и в ней создать файл files.sh с содержимым
```
#!/bin/bash
for i in {1..12}
do
  touch "res-$i.txt"
  echo "Created at $(date +%s)" >> res-$i.txt
done
```
9) Сделать файл файл files.sh исполняемым для всех
10) Выполнить команду ```./files.sh```
11) В директории temp найти все файлы, в имени которых есть .txt
12) Удалить директорию temp
