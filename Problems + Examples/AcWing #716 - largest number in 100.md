```python
m = 0
ind = 1

for i in range(100):
    a = int(input())
    if a > m:
        m = a
        ind = i + 1
        
print(m)
print(ind)
```