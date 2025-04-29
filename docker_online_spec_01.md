1) Запустить контейнер:
- image: caddy
- volumes: ```index.html:/usr/share/caddy/index.html```\
содержимое файла index.html
```
<h1>Hello caddy!</h1>
```
- ports: ```80:80```
- name: web-caddy-1\
Проверить работу приложения с помощью curl;\
Посмотреть логи контейнера;\
Зайти в контейнер и найти кофигурационный файл caddy;\
Остановить и удалить контейнер
2) Запустить с помощью docker compose следующую инфраструктуру
- 3 контейнера:
  - image: jmalloc/echo-server
  - имена: web1, web2, web3
  - в сети web-net
- контейнер с haproxy:
  - image:  haproxytech/haproxy-alpine
  - volume: ```./haproxy.cfg:/usr/local/etc/haproxy/haproxy.cfg```\
 содержимое файла haproxy.cfg
```
  global
    stats socket /var/run/api.sock user haproxy group haproxy mode 660 level admin expose-fd listeners
    log stdout format raw local0 info

  defaults
    mode http
      timeout client 10s
      timeout connect 5s
      timeout server 10s
      timeout http-request 10s
      log global
  frontend stats
    bind *:8404
    stats enable
    stats uri /
    stats refresh 10s

  frontend myfrontend
    bind :80
    default_backend webservers

  backend webservers
    server s1 web1:8080 check
    server s2 web2:8080 check
    server s3 web3:8080 check
```
  - порты: ```80:80``` и ```8404:8404```
  - в сети web-net

Проверить работу:
- при обращении на порт 80
<img width="996" alt="image" src="https://github.com/user-attachments/assets/0e26f7d4-299e-4671-86ae-beeebf30a430" />

- при обращении на порт 8404
<img width="1197" alt="image" src="https://github.com/user-attachments/assets/be4ffe3f-4260-41af-a5c0-0c69be4081af" />
