very important concept in functional programming

fundamental part of recursion is self-reference: functions calling themselves. It is used to solve problems that can be broken up into easier sub-problems of the type(Fibonacci!)

Classic example of function that is implemented recursively is the factorial function.

i.e. 5! = 5 \* 4 \* 3 \* 2 \* 1. to implement this, use the equation n! = n \* (n-1)!(duh)

furthermore, 1! = 1, which counts as a base case, as it can be calculated w/o performing any more factorials.

```python
#i.e.
def factorial(x):
	if x == 1:
		return 1
	else:
		return x * factorial(x - 1)

print(factorial(5))
```

the base case acts as the exit condition of the recursion

recursive calls can be infinite, like infinite while loops. These often occur when you forget to implement the base case, causing a deadlock

```python
#i.e. incorrect version of factorial function
def factorial(x):
	return x * factorial(x - 1)

print(factorial(5))
#will result in RuntimeError w/o base case
```

recursion can also be indirect. 1 function can call a second, which calls the first, which calls the second, and so on. This can occur with any number of functions

```python
#i.e.
def is_even(x):
	if x == 0:
		return True
	else:
		return is_odd(x-1)

def is_odd(x):
	return not is_even(x)
```