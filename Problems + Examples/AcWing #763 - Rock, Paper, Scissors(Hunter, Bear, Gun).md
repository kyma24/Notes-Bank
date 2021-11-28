```python
n = int(input())

r = ["Hunter", "Bear", "Gun"]
for i in range (n):
    p1, p2 = input().split()

    r1 = r.index(p1)
    r2 = r.index(p2)

    if r1 == r2:
        print ("Tie")
    elif (r1 + 1) % 3 == r2:
        print ("Player2")
    else:
        print ("Player1")
```