1) Написать скрипт, который получает следующую информацию о процессе dockerd:
- pid процесса
- статус процесса
- ppid процесса
вывести полученный результат в файл dockerd_info в формате
```
dockerd: PID=$PID PPID=$PPID STATUS: $STAT
```
например
```
dockerd PID=1422 PPID=1 STATUS: Ssl
```
2) Написать скрипт, который получает следующую информацию о процессоре
- количество ядер (команда nproc --all)
- модель (найти значение model name в /proc/cpuinfo)
- max частоту (найти значение Max Speed в выводе команды sudo dmidecode -t 4)
вывести полученный результат в файл cpu_info в формате
```
$hostname cpu details: Cores: $CORES Model: $MODEL Speed: $SPEED
```
например
```
server-1 cpu details: Cores: 2 Model: Intel Xeon Processor (Icelake) Speed: 2000 MHz
```
