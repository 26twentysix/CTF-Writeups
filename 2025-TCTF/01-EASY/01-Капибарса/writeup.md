# Капибарса

![img.png](task%2Fimg.png)

На прикрепленной картинке схемка с лего робота с программой, которая шифрует цвета в цифры\
Пишем небольшую прогу что бы расшифровать\
```python
val = 414363270630243
letters = 'GBRY'
flag = ''
while val != 1:
    flag += letters[val % 4]
    val //= 4

print('tctf{' + flag[::-1] + '}')
```
tctf{BYRGYBYGBYBYRGYBYGRYBRGY}