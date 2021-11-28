```py
def fib(f):
    if f == 1:
        return 0
    elif f == 2:
        return 1
    else:
        return fib(f-1) + fib(f-2)

f = eval(input("Please enter the position of the term. "))
print("The #", f, " term of the fibonacci sequence is ", fib(f), ".")
```
```py
# w/ list instead.
n = int(input("n = "))

fib_sequence = [0, 1, 1]

for i in range(3, n + 1):
	fib_sequence.append(fib_sequence[i - 1] + fib_sequence[i - 2])

print(fib_sequence[n] - 1)
```