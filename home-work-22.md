# Теоретический блок
Почти весь базовый синтаксис bash-скриптов: https://youtu.be/kEpCiCb-y1Y

Примеры скриптов
- https://youtu.be/4myfKzBl_jc (попроще)
- https://youtu.be/qMFb7Nj_WA4 (посложнее)
- https://youtu.be/NdvT8sAdllw (попроще)

# Практика
#### 1) Написать скрипт для получения информации о пользователях -- в файл users_info нужно вывести информацию о своем пользователе:
- имя пользователя
- UID
- все группы, в которых состоит пользователь
- оболочка
формат
```
$(hostname) [component: USERS] User - $username UID - $USER_ID Group list - $groups Shell - $USER_SHELL
```
например
```
server-1 User - anestesia UID - 1000 Group list - sudo,docker Shell - /bin/bash
```
#### 2) Написать скрипт для получения информации об оперативной памяти в файл mem_info
- значение Total online memory из вывода команды lsmem
- значение available из вывода команды free -h
формат
```
$(hostname) [$(date)] [component: MEM] Total memory - $mem Available mem - $av_mem
```
например
```
server-1 [Wed Feb 19 05:27:03 AM UTC 2025] [component: MEM] Total memory - 4G Available mem - 3.2Gi
```
#### 3) Написать скрипт для создания рабочей директории проекта в /opt/projects со следующей структурой
- имя проекта devops-app
- содержимое devops-app
  - src/
  - docs/
  - media/
  - README.md
  - LICENSE

то есть по итогу работы скрипта должно получиться следующее:
<img width="538" alt="image" src="https://github.com/user-attachments/assets/cfa6f82f-7cb9-4346-a8cc-1c8b488b3b0a" />

#### 4) Написать скрипт для сбора информации о процесе dockerd (подсказка ```ps -o %cpu,%mem -p $PID```:
- % использования cpu 
- % использования mem
- command

вывести информацию в файл process_info.log в формате
```
$(hostname) [$(date)] [component: PROCESS] Running $command with resource usage: cpu - $cpu_usage memory - $mem_usage
```
например
```
server-1 [Wed Feb 19 05:42:14 AM UTC 2025] [component: PROCESS] Running dockerd with resource usage: cpu - 0.0 memory - 2.1
```
#### 5) Написать скрипт, который будет получать сколько процентов диска использовано (команда df) и делать запись в файл /var/log/disk_space.log, если это число превысило 80%
#### 6) Написать скрипт, который автоматизирует создание пользователя:
- имя пользователя передается скрипту как аргумент
- при создании пользователя обязательно создать ему домашнюю директорию и установить интерпретатор /bin/bash
- сгенерировать пароль и установить его пользователяю
- вывести в файл creation_users.log информацию:
  - имя созданного пользователя
  - id созданного пользователя (UID)
  - пароль, установленный пользователю

формат
```
$(hostname) [$(date)] [component: USERS] Created user $USER_NAME with id $US_ID and password $PASS
```
например
```
server-1 [Wed Feb 19 05:42:14 AM UTC 2025] [component: USERS] Created user ansible with id 1005 and password P6kMIZ9Snc
```
#### 7) Написать скрипт, который будет проверять состояние указанных служб и перезапускать их, если они остановлены. Имя службы передавать скрипту как аргумент
#### 8) Написать скрипт для поиска свободных портов из заданного пользователем диапазона
