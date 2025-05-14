1) В нашем php-products заменить image приложения на `anestesia01/demo:php-products` (https://hub.docker.com/repository/docker/anestesia01/demo/general) и запустить проект с помощью `docker compose`
2) Проверить работу с помощью `curl`, если овет похож на такой, то все ок
```
<!-- index.php -->
<!DOCTYPE html>
<html>
<head>
    <title>Product List</title>
</head>
<body>
    <h1>Products</h1>
    <table border="1">
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Price</th>
        </tr>
                <tr>
            <td>1</td>
            <td>Laptop</td>
            <td>999.99</td>
        </tr>
                <tr>
            <td>2</td>
            <td>Smartphone</td>
            <td>499.99</td>
        </tr>
                <tr>
            <td>3</td>
            <td>Headphones</td>
            <td>149.99</td>
        </tr>
            </table>
</body>
</html>
```
3) Написать bash скрипт, который будет делать резервную копию БД postgres нашего приложения
