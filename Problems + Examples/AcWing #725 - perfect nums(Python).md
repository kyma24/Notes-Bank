```python
n = int(input())
for i in range(0, n):
    x = int(input())
    if x == 1:
        print("1 is not perfect")
        continue
    s = 0
    j = 1
    while j*j <= x:
        if j == 1:
            s = s + 1
        elif j*j == x:
            s = s + j
        elif x % j == 0:
            s = s + j + int(x/j)
        j += 1
    if s == x:
        print(x, "is perfect")
    else:
        print(x, "is not perfect")
```