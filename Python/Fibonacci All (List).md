```py
#calculates the first n numbers in the fib sequence
num = int(input())

def fibonacci(n):
	list = []

	for i in range (0, n):
		if i <= 1:
			list.append(i)
		elif i == 2:
			list.append(1)
		else:
			list.append(list[i-1] + list[i-2])
	return list

fibs = fibonacci(num)

for i in range(0, len(fibs)):
	print(fibs[i])
```