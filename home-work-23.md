### Теория
- что такое LEMP-стек: https://youtu.be/LpLWNUmGLY8
- что такое nginx: https://youtu.be/h6syPf_wpnQ
### Практика
Повторить все действия, которые мы делали на уроке на своей вируталке. Порядок действий:
- открыть репозиторий: https://github.com/AnastasiyaGapochkina01/simple_php_app
- установить:
  - php, php-fpm, php-mysql
  - nginx
  - mariadb (не забыть ```sudo mysql_secure_installation``` после установки)
  - git
- склонировать репозиторий в папку /var/www
- перейти в папку со склонированным проектом
- импортировать БД
```
mysql -u root -p < simple_data.sql
```
- скопировать файл конфига simple_app nginx в /etc/nginx/sites-available/simple_app
- удалить дефолтный конфиг nginx
- поправить конфиг приложения в /etc/nginx/sites-available/simple_app
  - должна быть указана правильная папка с проектом
  - правильный сокет php-fpm (проверить можно ```sudo ss -nlp | grep fpm```)
- проверить корректность конфига, перезагрузить конфиг
- проверить, что приложение работает


> [!WARNING]  
> Если все получится легко, то попробовать аналогично развернуть https://github.com/AnastasiyaGapochkina01/linux_app
