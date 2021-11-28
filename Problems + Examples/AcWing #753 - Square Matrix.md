```python
while True:
    n = int(input())

    if n == 0:
        break

    for i in range (1, n+1):
        for j in range (1, n+1):
            m = min (min(i, n - i + 1), min (j, n - j + 1))
            print (m, end = " ")
        print()
    print()
```