# SkyWave 1: High Tower 
![img.png](task%2Fimg.png) \
Подключаемся к дб, смотрим название таблиц, пишем скл запросик 
```mysql
select *
from Towers
where elevation > 219
  and elevation < 221;
```
![img.png](img.png) \
flag{215}