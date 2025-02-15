### Q2: Accumulate
题目的意思是先实现`accumulate`，再用这个来实现后两个

### Q3: Make Repeater
正常在内函数中，可以直接使用外函数的变量

但是，如果在内函数中有修改这个变量的动作，则会被认作是局部变量，导致NameError
```python
def make_repeater(f, n):
    def foo(x):
        while n > 0:  # ❌ 这里 Python 认为 n 是局部变量，但此时未定义
            x, n = f(x), n - 1  # ❌ 这里对 n 赋值了，所以 n 被视为局部变量
        return x
    return foo
```
如果想直接修改n，可以使用`nonlocal`关键字明确作用域

不过修改外函数变量可能会导致意外的副作用，答案中使用`k`作为计数器的方法更好
