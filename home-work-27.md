1) Запустить nodejs приложение без базы данных
- в директории /opt создать директорию nodejsapp и в ней создать файл server.js с содержимым
```
const http = require('http');

const port = 3000;

const server = http.createServer((req, res) => {
    res.statusCode = 200;

    res.setHeader('Content-Type', 'text/plain');

    res.end('Привет, мир!\n');
});

server.listen(port, () => {
    console.log(`Сервер запущен на порту ${port}`);
});
```
- запустить server.js с помощью systemd-юнита
  - проверить, на каком порту запустился сервис
- настроить nginx так, чтобы он перенаправлял входящие запросы на запущенное приложение
2) Запустить приложение на python:
- в домашней директории создать папку app
- в папке app создать файлы
init.sh
```
#!/usr/bin/env bash

apt update && apt install -y -q python3-venv python3-pip
python3 -m venv venv
source venv/bin/activate
python3 -m pip install -r requirements.txt
```
pyapp.service
```
[Unit]
Description=Flask App Service
After=network.target

[Service]
User=root
Group=www-data
WorkingDirectory=/path/to/app
Environment="PATH=/path/to/app/venv/bin"
ExecStart=/path/to/app/venv/bin/gunicorn --workers 3 --bind unix:/run/flask-app.sock -m 007 wsgi:app
Restart=on-failure

[Install]
WantedBy=multi-user.target
```
wsgi.py
```
from app import app

if __name__ == "__main__":
    app.run()
```
requirements.txt
```
gunicorn
flask
mariadb
```
app.py
```
from flask import Flask, request, jsonify
import mariadb

app = Flask(__name__)

config = {
    'host': '127.0.0.1',
    'port': 3306,
    'user': 'root',
    'password': 'root',
    'database': 'demo'
}

def connect_db():
    try:
        conn = mariadb.connect(**config)
        return conn
    except mariadb.Error as e:
        print(f"Ошибка подключения: {e}")
        return None

@app.route('/users', methods=['GET'])
def get_users():
    conn = connect_db()
    if conn is None:
        return jsonify({"error": "Ошибка подключения"}), 500

    cur = conn.cursor()
    cur.execute("SELECT * FROM users")
    rows = cur.fetchall()

    users = []
    for row in rows:
        user = {
            "id": row[0],
            "name": row[1],
            "email": row[2]
        }
        users.append(user)

    conn.close()
    return jsonify(users)

@app.route('/users', methods=['POST'])
def create_user():
    conn = connect_db()
    if conn is None:
        return jsonify({"error": "Ошибка подключения"}), 500

    data = request.json
    if "name" not in data or "email" not in data:
        return jsonify({"error": "Недостаточно данных"}), 400

    cur = conn.cursor()
    cur.execute("INSERT INTO users (name, email) VALUES (?, ?)", (data['name'], data['email']))
    conn.commit()
    conn.close()
    return jsonify({"message": "Пользователь создан"}), 201

@app.route('/users/<int:user_id>', methods=['PUT'])
def update_user(user_id):
    conn = connect_db()
    if conn is None:
        return jsonify({"error": "Ошибка подключения"}), 500

    data = request.json
    if "name" not in data and "email" not in data:
        return jsonify({"error": "Недостаточно данных"}), 400

    cur = conn.cursor()
    cur.execute("SELECT * FROM users WHERE id = ?", (user_id,))
    user = cur.fetchone()
    if user is None:
        return jsonify({"error": "Пользователь не найден"}), 404

    if "name" in data:
        cur.execute("UPDATE users SET name = ? WHERE id = ?", (data['name'], user_id))
    if "email" in data:
        cur.execute("UPDATE users SET email = ? WHERE id = ?", (data['email'], user_id))

    conn.commit()
    conn.close()
    return jsonify({"message": "Пользователь обновлён"}), 200

@app.route('/users/<int:user_id>', methods=['DELETE'])
def delete_user(user_id):
    conn = connect_db()
    if conn is None:
        return jsonify({"error": "Ошибка подключения"}), 500

    cur = conn.cursor()
    cur.execute("SELECT * FROM users WHERE id = ?", (user_id,))
    user = cur.fetchone()
    if user is None:
        return jsonify({"error": "Пользователь не найден"}), 404

    cur.execute("DELETE FROM users WHERE id = ?", (user_id,))
    conn.commit()
    conn.close()
    return jsonify({"message": "Пользователь удалён"}), 200

if __name__ == '__main__':
    app.run(debug=True)
```
- в файле pyapp.service поправить строки
```
WorkingDirectory=/path/to/app
Environment="PATH=/path/to/app/venv/bin"
ExecStart=/path/to/app/venv/bin/gunicorn --workers 3 --bind unix:/run/flask-app.sock -m 007 wsgi:app
```
нужно заменить __/path/to/app__ на путь к созданной директории app
- скопировать файл pyapp.service в /etc/systemd/system
- сделать файл init.sh исполняемым и запустить ```sudo ./init.sh```
- выполнить
```
sudo systemctl daemon-reloa
sudo systemctl start pyapp.service
sudo systemctl status pyapp.service
```
если status active, то проверить на чем "сидит" только что запущенное приложение
- создать в /etc/nginx/sites-available файл paypp с содержимым
```
server {
    listen 80;
    server_name example.com;

    location / {
        include proxy_params;
        proxy_pass http://unix:/run/flask-app.sock;
    }
}
```
- создать симинк на этот файл в /etc/nginx/sites-enabled
- проверить и перезагрузить конфигурацию nginx
- выполнить запрос
```
curl 127.0.0.1/users
```
если ответ выглядит так ```[]``` то все ок
