```py
def fib(n):
    fib_seq = []
    for i in range (0,n):
        if i <= 1:
            fib_seq.append (i)
        else:
            fib_seq.append(fib_seq[i-1] + fib_seq[i-2])
    return fib_seq[n-1]

print (fib(5))
```