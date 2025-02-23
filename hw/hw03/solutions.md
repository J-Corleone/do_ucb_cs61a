
### Q1

```py
n % 10 == 8 and 1 or 0
```
n为8时可返回1，否则返回0

### Q3
不让判断奇偶，那我多传一个参数标识奇偶

ans:
```py
def interleaved_sum(n, odd_func, even_func):
    def f(k):
        if k > n:
            return 0
        if k == n:
            return odd_func(k)
        return odd_func(k) + even_func(k+1) + f(k+2)
    return f(1)
```
答案的思路是：你知道1是奇数，写个内部函数，接受奇数k，对k应用odd_func，对k+1应用even_func，递归这个内部函数。

### Q4
本来不会，hint说和例题差不多，稀里糊涂的对了

相当于用微信钱包和小卖部换n元的现金，现金金额有：1, 5, 10, 20, 50, 100

小卖部有100币额时换的可能性+小卖部没有100时换的可能性

### Q6.Hanoi
先把上面的n-1个挪到中间
然后把第n个挪到end
再把n-1个挪到end

### Q7.Anonymous factorial func
？这变态吧，鬼能看懂了

**ans1:**
```py
(lambda f: lambda k: f(f, k))(lambda f, k: k if k==1 else k*f(f, k-1))

def f1(f):
    def g(k):
        return f(f, k)
    return g

def f2(f, k):
    if k==1:
        return k
    return k*f(f, k-1)
```
f2是f1传入的函数

**ans2:**
```py
(lambda f: f(f))(lambda f: lambda x: 1 if x==1 else x*f(f)(x-1))
```