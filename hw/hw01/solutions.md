### Q2: Two of Three
Write a function that takes three _positive_ numbers as arguments and returns the sum of the squares of the two smallest numbers. **Use only a single line for the body of the function.**

```python
def two_of_three(i, j, k):
    return min(i*i+j*j, i*i+k*k, j*j+k*k)
    # Alternate solution
def two_of_three_alternate(i, j, k):
    return i**2 + j**2 + k**2 - max(i, j, k)**2
```
我的太麻烦了

### Q3: Largest Factor
Write a function that takes an integer `n` that is **greater than 1** and returns the largest integer that is smaller than `n` and evenly divides `n`.
```python
def largest_factor(n):
    factor = n - 1
    while factor > 0:
        if n % factor == 0:
            return factor
        factor -= 1
```
没注意n是大于1的，反着来就行