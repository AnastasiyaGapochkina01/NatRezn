1) Дан код на golang\
main.go
```
package main

import (
    "fmt"
    "log"
    "net/http"
    "time"
)

func helloHandler(w http.ResponseWriter, r *http.Request) {
    if r.URL.Path != "/" {
        http.Error(w, "404 Not Found", http.StatusNotFound)
        return
    }

    currentTime := time.Now().Format(time.RFC3339)
    greeting := "Hello!"

    fmt.Fprintf(w, "Current time: %s\n%s", currentTime, greeting)
}

func main() {
    http.HandleFunc("/", helloHandler)

    fmt.Println("Server started on 9100")
    log.Fatal(http.ListenAndServe(":9100", nil))
}
```
Необходимо собрать для него docker image. Для того чтобы код запустился нужно собрать его командой ```go build -o main main.go```. Запуск осуществляется простым запуском файла main
- собрать docker image
- запушить его в свой docker hub
- запустить контейнер, пробросив порт 9100 хоста на порт 9100 контейнера
- проверить работоспособность комнандой curl 127.0.0.1:9100 . Если отдается что-то похожее на это, то все ок
```
anestesia@projects-dev:~/golang$ curl 127.0.0.1:9100/
Current time: 2025-04-12T03:22:10Z
Hello!
```

2) Дан код на python:
```
import http.server
import socket
import os
import getpass

# Получаем имя пользователя
username = getpass.getuser()

# Получаем версию ОС
os_version = f"{os.sys.platform} {os.sys.version}"

s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.connect(("8.8.8.8", 80))
local_ip = s.getsockname()[0]
s.close()

greeting = f"Привет, {username}!"

class RequestHandler(http.server.BaseHTTPRequestHandler):
    def do_GET(self):
        if self.path != "/":
            self.send_response(404)
            self.send_header("Content-type", "text/plain")
            self.end_headers()
            self.wfile.write(b"404 Not Found")
            return

        self.send_response(200)
        self.send_header("Content-type", "text/plain")
        self.end_headers()

        response = f"Версия ОС: {os_version}\nПриветствие: {greeting}\nЛокальный IP: {local_ip}"
        self.wfile.write(response.encode())

def run_server():
    server_address = ('', 3000)
    httpd = http.server.HTTPServer(server_address, RequestHandler)
    print("Сервер запущен на порту 3000")
    httpd.serve_forever()

if __name__ == "__main__":
    run_server()
```
Необходимо собрать для него docker image. Запуск осуществляется командой ```python app.py```
- собрать docker image
- запушить его в свой docker hub
- запустить контейнер, пробросив порт 3000 в контейнере на порт 3000 на хосте
проверить работоспособность комнандой curl 127.0.0.1:3000 . Если отдается что-то похожее на это, то все ОК
```
anestesia@projects-dev:~$ curl 127.0.0.1:3000
Версия ОС: linux 3.9.2 (default, Mar 20 2025, 02:07:39)
[GCC 10.2.1 20210110]
Приветствие: Привет, anestesia!
Локальный IP: 10.129.0.25
```

3) Дан код на nodejs\
server.js
```
const http = require('http');

let requestCount = 0;

const server = http.createServer((req, res) => {
    requestCount++;
    res.writeHead(200, {'Content-Type': 'text/plain'});
    res.end(`Количество запросов: ${requestCount}`);
});

server.listen(3000, () => {
    console.log('Сервер запущен на порту 3000');
});
```
Необходимо собрать для него docker image. Для работы приложения требуется установить зависимости командой npm install. Код запускается командой ```node server.js```
- собрать docker image
- запушить его в свой docker hub
- запустить контейнер, пробросив порт 3000 в контейнере на порт 3030 на хосте
проверить работоспособность комнандой curl 127.0.0.1:3030. Если отдается что-то похожее на это, то все ОК
```
anestesia@projects-dev:~/php$ curl 127.0.0.1:3000
Количество запросов: 1
```
