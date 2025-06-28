1) Дан код на python
```
from flask import Flask
import sys
import os

app = Flask(__name__)

@app.route('/')
def index():
    python_version = sys.version
    current_directory = os.getcwd()
    return f"Версия Python: {python_version}\nТекущая директория: {current_directory}"

if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0')
```
Необходимо собрать для него docker image. Для работы приложения требуется установить flask командой ```pip install --no-cache-dir flask```. 
Запуск осуществляется командой ```python app.py```\
Задача:
- собрать docker image
- запушить его в свой docker hub
- запустить контейнер, пробросив порт 5000 в контейнере на порт 5000 на хосте
- проверить работоспособность комнандой ```curl 127.0.0.1:5000```. Если отдается что-то похожее на
```
anestesia@projects-dev:~$ curl 127.0.0.1:5000
Версия Python: 3.9.2 (default, Mar 20 2025, 02:07:39)
[GCC 10.2.1 20210110]
Текущая директория: /home/anestesia/python
```
то все ОК

2) Дан код на nodejs:
- server.js
```
const http = require('http');
const os = require('os');
const childProcess = require('child_process');

const getNodeVersion = () => {
    return childProcess.execSync('node -v').toString().trim();
};

const getOSVersion = () => {
    return os.type() + ' ' + os.release();
};

const server = http.createServer((req, res) => {
    const nodeVersion = getNodeVersion();
    const osVersion = getOSVersion();

    res.writeHead(200, {'Content-Type': 'text/plain'});
    res.end(`Версия Node.js: ${nodeVersion}\nВерсия ОС: ${osVersion}`);
});

server.listen(3000, () => {
    console.log('Сервер запущен на порту 3000');
});
```
- package.json
```
{
  "name": "node-info-app",
  "version": "1.0.0",
  "description": "",
  "main": "server.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "anestesia",
  "license": "ISC",
  "dependencies": {
    "express": "^4.21.1"
  },
  "scripts": {
	  "start": "node server.js"
  }
}
```
Необходимо собрать для него docker image. Для работы приложения требуется установить зависимости командой ```npm install```. Запуск осуществляется командой ```npm start```
Задача:
- собрать docker image
- запушить его в свой docker hub
- запустить контейнер, пробросив порт 3000 в контейнере на порт 3030 на хосте
- проверить работоспособность комнандой ```curl 127.0.0.1:3030```. Если отдается что-то похожее на
```
anestesia@projects-dev:~/node-server$ curl 127.0.0.1:3002
Версия Node.js: v23.11.0
Версия ОС: Linux 5.10.0-19-amd64
```
то все ОК
