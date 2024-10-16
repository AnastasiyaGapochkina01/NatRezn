1) В домашней директории создать папку text_processing и перейти в нее
2) Создать файл info.csv с таким содержимым
```
Name:Company:Price:Ganre:Multiplayer
Item1:Company1:60000$:Ganre1:Yes
Item2:Company2:70000$:Ganre2:Yes
Item3:Company3:90000$:Ganre1:Yes
Item4:Company4:90000$:Ganre1:No
Item5:Company5:110000$:Ganre1:Yes
Item6:Company6:410000$:Ganre2:Yes
Item7:Company1:60000$:Ganre1:Yes
Item8:Company4:40000$:Ganre2:No
Item9:Company3:90000$:Ganre1:Yes
```
3) В файле info.csv с помощью grep найти строки, которые содержат слово No
4) Вывести третью и четвертую строки файла info.csv
5) В файле info.csv найти все строки, в которых встречается слово Ganre2
6) В файле info.csv найти все строки, в которых встречается слово Ganre2 и вывести только 3 поле
7) Создать файл metrics с содержимым
```
metric_name:metric_type:interval
cache_disk_use:gauge:1
cache_use:gauge:0
key_buffer_bytes_used:byte:3
table.rows.read:count:10
disk_use:gauge:10
data_size:gauge:1
rows_deleted:count:1
bytes_received:byte:1
```
8) В файле metrics найти все строки, в которых встречается слово gauge и вывести только первое поле
9) В файле metrics найти все строки, в которых встречается слово byte и вывести только 3 поле
10) В файле metrics найти все строки, в которых встречается слово disk и вывести только 2 поле
11) В файле metrics найти все строки, которые *начинаются* с cache
12) В файле info.csv найти все строки, которые содержат слово Company4
13) В директории text_processing создать файл products с содержимым
```
Handle:Title:SKU:Location:On hand:Available:Count
product-1:Product A:PROD-A:Warehouse A:100
product-1:Product A:PROD-A:Warehouse A:50
product-2:Product B:PROD-B:Warehouse B:200
product-2:Product B:PROD-B:Warehouse B:150
product-3:Product C:PROD-C:Warehouse C:300
product-4:Product D:PROD-D:Warehouse A:400
product-4:Product D:PROD-D:Warehouse A:250
product-5:Product E:PROD-E:Warehouse B:500
product-5:Product E:PROD-E:Warehouse B:300
product-6:Product F:PROD-F:Warehouse C:600
product-6:Product F:PROD-F:Warehouse C:400
```
14) С помощью grep найти в файле products все строки, содержащие слово PROD-C
15) С помощью grep найти в файле products все строки, содержащие слово product-3 и вывести для них последний столбец
16) Вывести 5, 6 и 7 строки файла products
