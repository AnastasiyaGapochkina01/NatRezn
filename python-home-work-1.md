1) Написать программу, которая запрашивает у пользователя следующие данные
- имя персонажа
- его возраст
- предмет, который персонаж возьмет на старте\
и выведет их на экран в формате
```
Your character is NAME:
- age: AGE
- inventory: THING
```
где
- NAME - имя, которое ввел пользователь
- AGE - возраст, который ввел пользователь
- THING - вещь, которую выбрал пользователь
2) Дополнить программу из задания №1 так, чтобы в ней была заданы (не введены пользователем) переменные
- power со значением 200
- переменная coins со значением 0
- переменная health со значением 150
а программа выводила следуюущю информацию
```
Your character is NAME:
- age: AGE
- inventory: THING
- power: 200
- health: 150
- coins: 0
```
где
- NAME - имя, которое ввел пользователь
- AGE - возраст, который ввел пользователь
- THING - вещь, которую выбрал пользователь
3) Дополнить программу из задания №2 так, чтобы после выводилась строк
```
NAME met wizard Merlin. Merlin gave him a magic map 
```
где
- NAME - имя, которое ввел пользователь\
а потом задавалась переменная с именем character_stuff и значением "magic map"
4) Дополнить программу из задания №3 так, чтобы выводилась строка
```
After a long journey, NAME found a hut. After searching it, he found 5 coins and a bottle with an unknown potion.
```
где
- NAME - имя, которое ввел пользователь\
значение переменной coins увеличивалось на 5, а переменная inventory содержала бы теперь предмет, который взял пользователь на старте и строку "bottle of potion"\
вывести на экран строку
```
Now NAME have COUNT coins, STUFF
```
где
- NAME - имя, которое ввел пользователь
- STUFF - все вещи, которые теперь есть у пользователя
- COUNT - количество монет
5) Дополнить программу из задания №4 так, чтобы выводилась строка
```
NAME met a big angry griffon! Would he fight (enter 1) or leave (enter 2)?
```
где
- NAME - имя, которое ввел пользователь\
считать решение пользователя. если он ввел 1, то 
- отнять от переменной 30 от переменной health
- отнять 15 от переменной power
- вывести строку (все цифры подставлять через обращение к переменным)
```
NAME won, but he was very tired and the griffin dealt him 30 points of damage and 15 points of power. Now he has 120 points of health and 185 points od power
```
где
- NAME - имя, которое ввел пользователь\
6) Дополнить программу из задания №5 так, чтобы выводилась строка
```
Welcome to the King Arthur's Castle, NAME! Now you shoid choose door (1/2/3):
```
где
- NAME - имя, которое ввел пользователь

считать пользовательский выбор и реализовать сценарии
- 1 - если персонаж выбирает первую дверь, то у него появляется союзник - рыцарь. задать переменную companion со значением knight
- 2 - если персонаж выбирает вторую дверь, то встречает привидение, которое предлагает решить его загадку (загадку придумать самостоятельно):\
  - если герой угадывает ответ, то привидение дает ему 10 монет (не забыть увеличить количество монет у персонажа)
  - если нет, то привидение насылает на персонажа проклятие. добавить переменную ghost_label со значением curse
- 3 - если персонаж выбирает третью дверь, то встречает вампира, который спит в комнате с сокровищами. персонажу надо решить, попытается ли он утащить несколько монет или же просто уйти:
  - если персонаж решает уйти, то ничего не происходит
  - если персонаж решает утащить несколько монет, то вампир просыпается и съедает персонажа
7) вывсети актуальную информацию о персонаже в произвольной форме
