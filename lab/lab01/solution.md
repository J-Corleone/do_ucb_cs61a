### Q1: Return and Print
```python
>>> def welcome():
...     print('Go')
...     return 'hello'
>>> def cal():
...     print('Bears')
...     return 'world'
>>> welcome()
(line 1)? Go
(line 2)? 'hello'
-- OK! --

>>> print(welcome(), cal())
(line 1)? Go
(line 2)? Bears
(line 3)? hello world
-- OK! --
```
### Q2: Debugging Quiz
```python
Q: In the following traceback, what is the most recent function call?
Traceback (most recent call last):
    File "temp.py", line 10, in <module>
      f("hi")
    File "temp.py", line 2, in f
      return g(x + x, x)
    File "temp.py", line 5, in g
      return h(x + y * 5)
    File "temp.py", line 8, in h
      return x + 0
  TypeError: must be str, not int
Choose the number of the correct choice:
0) h(x + y * 5)
1) g(x + x, x)
2) f("hi")
? 0
-- OK! --

Q: When should you use print statements?
Choose the number of the correct choice:
0) To investigate the values of variables at certain points in your code
1) For permanant debugging so you can have long term confidence in your code
2) To ensure that certain conditions are true at certain points in your code
? 0
-- OK! --

Q: Which of the following is NOT true?
Choose the number of the correct choice:
0) It is generally bad practice to release code with debugging print statements left in
1) Debugging is not a substitute for testing
2) It is generally good practice to release code with assertion statements left in
3) Testing is very important to ensure robust code
4) Code that returns a wrong answer instead of crashing is generally better as it at least works fine
? 4
-- OK! --
```

### Q3: Pick a Digit
Implement `digit`, which takes positive integers `n` and `k` and has only a single return statement as its body. It returns the digit of `n` that is `k` positions to the left of the rightmost digit (the one's digit). If `k` is 0, return the rightmost digit. If there is no digit of `n` that is `k` positions to the left of the rightmost digit, return 0.

**Hint:** Use `//` and `%` and the built-in `pow` function to isolate a particular digit of `n`.

---
```python
def digit(n, k):
    return n // pow(10, k) % 10
```
没想起来一行的咋写😿

### Q4: Middle Number
Implement `middle` by writing a single return expression that evaluates to the value that is neither the largest or smallest among three different integers `a`, `b`, and `c`.

**Hint:** Try combining all the numbers and then taking away the ones you don't want to return.

---
```python
def middle(a, b, c):
    return a + b + c - min(a, b, c) - max(a, b, c)
```
这个我的也过了

### Q6: Falling Factorial
Let's write a function `falling`, which is a "falling" factorial that takes two arguments, `n` and `k`, and returns the product of `k` consecutive numbers, starting from `n` and working downwards. When `k` is 0, the function should return 1.

---
```python
def falling(n, k):
    total, stop = 1, n-k
    while n > stop:
        total, n = total*n, n-1
    return total
```
这个stop🤨


### Q10: Double Eights
Write a function that takes in a number and determines if the digits contain two adjacent 8s.

----
```python
def double_eights_alt(n):
    while n:
        if n % 10 == 8 and n // 10 % 10 == 8:
            return True
        n //= 10
    return False
```
