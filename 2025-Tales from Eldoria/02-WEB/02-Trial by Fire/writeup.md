# Trial by Fire


Начинаем игру, видим менюшку с возможными действиями и спрятанную в коде страницы кнопку Ancient Capture Device\
Для ее активации вводим конами код, жмакаем и получаем подсказку что у нас тут Jinja SSTI\
(К такому же выводу можно придти посмотрев на код приложения)
![img_4.png](img_4.png)\
Начинаем новую игру, в строку имени впихиваем иньекцию (ограничение на количество символов можно убрать в коде страницы)\
![img_5.png](img_5.png)\
Проигрываем быстренько игру и получаем флаг\
![img_6.png](img_6.png)