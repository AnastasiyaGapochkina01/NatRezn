1) В директории docker-data создать директорию httpd-data. В httpd-data создать 
- файл index.html с содержимым
```
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Велосипедный Магазин</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Bike Shop</h1>
        <nav>
            <ul>
                <li><a href="#bikes">Велосипеды</a></li>
                <li><a href="#accessories">Аксессуары</a></li>
                <li><a href="#service">Сервис</a></li>
                <li><a href="#contact">Контакты</a></li>
            </ul>
        </nav>
    </header>

    <section id="hero">
        <h2>Добро пожаловать в наш магазин!</h2>
        <p>Мы предлагаем широкий выбор велосипедов для любого стиля езды и бюджета.</p>
        <button><a href="#bikes">Посмотреть велосипеды</a></button>
    </section>

    <section id="bikes">
        <h2>Велосипеды</h2>
        <div class="bike">
            <img src="bike1.jpg" alt="Городской велосипед">
            <p>Городской велосипед</p>
            <p>Цена: 20 000 руб.</p>
        </div>
        <div class="bike">
            <img src="bike2.jpg" alt="Горный велосипед">
            <p>Горный велосипед</p>
            <p>Цена: 30 000 руб.</p>
        </div>
        <div class="bike">
            <img src="bike3.jpg" alt="Шоссейный велосипед">
            <p>Шоссейный велосипед</p>
            <p>Цена: 40 000 руб.</p>
        </div>
    </section>

    <section id="accessories">
        <h2>Аксессуары</h2>
        <ul>
            <li>Шлемы</li>
            <li>Перчатки</li>
            <li>Замки</li>
            <li>Велосипедные колокольчики</li>
        </ul>
    </section>

    <section id="service">
        <h2>Сервис</h2>
        <p>Мы предлагаем услуги по ремонту и обслуживанию велосипедов.</p>
    </section>

    <section id="contact">
        <h2>Контакты</h2>
        <p>Телефон: +7 123 456 78 90</p>
        <p>Email: <a href="mailto:info@example.com">info@example.com</a></p>
        <p>Адрес: ул. Ленина, 1</p>
    </section>

    <footer>
        <p>&copy; 2023 Велосипедный Магазин</p>
    </footer>
</body>
</html>
```
- файл style.css с содержимым
```
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

header {
    background-color: #333;
    color: #fff;
    padding: 20px;
    text-align: center;
}

nav ul {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: space-between;
}

nav a {
    color: #fff;
    text-decoration: none;
}

#hero {
    background-image: url('background.jpg');
    background-size: cover;
    height: 300px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: #fff;
}

#hero button {
    background-color: #333;
    color: #fff;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
}

.bike {
    display: inline-block;
    margin: 20px;
    width: 200px;
}

.bike img {
    width: 100%;
    height: 150px;
    object-fit: cover;
}

footer {
    background-color: #333;
    color: #fff;
    padding: 10px;
    text-align: center;
    clear: both;
}
```
2) Запустить контейнер с именем bike-web и с:
- сопоставлением директории ./httpd-data на хосте с директорией /usr/local/apache2/htdocs в контейнере
- сопоставлением порта 8080 хоста с портом 80 контейнера
- docker image: httpd:2.4
Все прошло успешно, если при обращении на публичный ip и порт 8080 показывается такое

<img width="836" alt="image" src="https://github.com/user-attachments/assets/af036e69-57ee-4782-9f09-526a5ae78d5f" />

3) В директорию docker-data склонировать репозиторий https://github.com/AnastasiyaGapochkina01/sample-ruby-app/tree/main
4) Запустить контейнер с именем ruby-app и с:
- сопоставлением директории sample-ruby-app с директорией /usr/src/app в контейнере
- сопоставлением порта 8000 хоста с портом 3000 контейнера
5) Зайти в контейнер sample-ruby-app, перейти в директорию /usr/src/app и выполнить команды
```
bundle install --jobs=3 --retry=3
bundle exec rackup --host 0.0.0.0
```
Все прошло успешно, если при обращении на публичный ip и порт 8000 показывается ```Hello world```
