1) Из файла /proc/meminfo получить все строки. относящиеся к HugePages
2) С помощью awk вывести из файла /etc/passwd имена всех пользователей (первое поле)
3) Отфильтровать вывод команды free -h так, чтобы получить размер свободной (available) памяти
4) Отфильровать вывод команды lscpu так, чтобы получить значение CPU MHz
5) Отфильровать вывод команды lscpu так, чтобы получить значение Hypervisor vendor
6) Выполнить команду lsmod и в выводе найти строку, которая содержит информацию о модуле overlay
7) Выполнить команду lsmod и в выводе найти строку, которая содержит информацию о модуле floppy и вывести второй столбец (это размер модуля)
8) Найти в файле /proc/cpuinfo информацию о модели процессора
9) Перейти в директорию text_processing и выполнить команду
```
wget https://raw.githubusercontent.com/AnastasiyaGapochkina01/NatRezn/refs/heads/main/files/access.log
```
после ее выполнения в директории должен появиться файл access.log

10) Выполнить head access.log, в файле должны быть строки вида
```
192.168.1.1,[17/Oct/2024:10:00:00 +0000],"GET /index.html HTTP/1.1",200,512,"-","Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/62.0.3202.94 Safari/537.36"
192.168.1.2,[17/Oct/2024:10:01:00 +0000],"POST /api/data HTTP/1.1",201,256,"http://example.com","Mozilla/5.0 (Linux; Android 9; Pixel 3 XL) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.111 Mobile Safari/537.36"
192.168.1.3,[17/Oct/2024:10:02:00 +0000],"GET /about.html HTTP/1.1",404,0,"http://example.com/index.html","Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/13.0 Safari/605.1.15"
```

<img width="920" alt="image" src="https://github.com/user-attachments/assets/7840c372-a890-4622-a7aa-8a64b1ccb653">

11) Найти в файле access.log записи, в которых код ответа 404
12) Найти в файле access.log записи, в которых код ответа 500
13) Найти в файле access.log записи, в которых код ответа 200 и вывести только IP (первое поле)
14) Найти в файле access.log записи, в которых метод запроса POST
15) Найти в файле access.log записи, в которых метод запроса PATCH и вывести ip и код ответа
16) Найти в файле access.log записи, в которых есть подстрока Android 10
