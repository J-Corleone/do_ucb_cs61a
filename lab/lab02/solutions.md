### WWPD
```py
>>> None or ""
''
>>> "" or None

>>> (lambda: 3)()
3

>>> b = lambda x, y: lambda: x + y
>>> c = b(8, 4)
>>> c
<function <lambda>.<locals>.<lambda> at 0x7fbbe930d240>
>>> c()
12
```

### Q7
a, b的最小公倍数 = a * b / (a, b)

标准答案是，这个最小公倍数能同时整除a, b
```py
n = 1
while True:
    if n % a == 0 and n % b == 0:
        return n
    n += 1
```
