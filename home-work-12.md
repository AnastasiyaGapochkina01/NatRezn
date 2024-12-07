# Работа с процессами
1) В домашней директории создать директорию servers
2) В директории server создать файл simple-server с содержимым
```
#!/bin/bash
LOG_FILE="simple_server.log"

log() {
    echo "$(date '+%Y-%m-%d %H:%M:%S') - $1" >> "$LOG_FILE"
}

if command -v nc >/dev/null 2>&1; then
  log "Skipping..."
else
  if sudo apt-get update && sudo apt-get install -y netcat; then
    log "Succees"
  else
    log "Error when install netcat"
  fi
fi

PORT=8082
while :; do
  { echo -ne "HTTP/1.1 200 OK\r\nContent-Length: $(echo -n "Hello, World!")\r\n\r\nHello, World!"; } | nc -l -p "$PORT" >> simple_server.log 2>&1
done
```
3) Выполнить команду ```./simple-server &> /dev/null &```
4) Найти id процесса simple-server
5) Выполнить команду ```curl 127.0.0.1:8082```
6) Проверить, появился ли в директории servers файл simple_server.log, посмотреть его содержимое
7) В директории /proc найти каталог, который соответствует найденному выше процессу simple-server
8) Запустить top и найти в нем процесс simple-server
9) Приостановить процесс simple-server
10) Вернуть из паузы процесс simple-server
11) Убить процесс simple-server
# Пользователи и права доступа
1) Создать пользователей cherry и peach
2) Проверить, существует ли группа admins, если нет - создать
3) Добавить пользователей cherry и peach в группу admins
4) Получить информацию о пользователе peach с помощью команды ```id```
5) В директории home_works создать директорию secret_files и назначить ее владельцем пользователя root, а группой - admins
6) Назначить права на директорию secret_files так, чтобы владелец и группа имели все права, все остальные не имели никаких прав доступа к ней
7) Создать в директории secret_files файл .secret1 с содержимым
```
admin:$2y$05$m5IrWlkAmnZOLmf4LZiSvuVXaVXK8w9I8f/5RPJDjeSpQgFJD0bXO
```
8) Назначить владельцем файла .secret1 пользователя cherry, а группой - admins
9) Создать в директории secret_files пустой файл .secret2
10) Назначить владельцем файла .secret2 пользователя peach, а группой - admins
11) Назначить права на файлы .secret1 и .secret2 так чтобы никто кроме владельцев не имел к ним никакого доступа
