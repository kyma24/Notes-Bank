creating a function(using def) normally assigns it to a variable automatically.

this is different from the creation of other objects like strings and integers, which can be created on the fly, without assigning them to a variable.

the same is possible with functions, provided that they are created using **lambda** syntax. Functions created this way are known as **anonymous**.

```python
def my_func(f, arg):
	return f(arg)

my_func(lambda x: 2*x*x, 5) 
```

This approach is more commonly used when passing a simple function as an argument to another function. The syntax is shown & consists of the lambda keyword followed by a list of arguments, a colon, and the expression to evaluate and return.

Lambda functions get their name from lambda calculus, which is a model of computation invented by Alonzo Church.

These lambda functions aren't as powerful as named functions.

They can only do things that require a single expression, usually equivalent to a single line of code.

```python
#i.e.
#named function
def polynomial(x):
	return x**2 + 5*x + 4
print(polynomial(-4))

#lambda
print((lambda x: x**2 + 5*x + 4)(-4))
```

In this code, we created an anonymous function on the fly and called it w/ an argument.

```python
#i.e.
a = (lambda x: x*x)(8)
#this creates a lambda function that returns the square of its argument and calls it for the number 8
```

lambda functions can be assigned to variables, and used like normal functions.

```python
double = lambda x: x*2
print(double(7))
```

however, there usually isn't a good reason to do this - it is usually better to define a function w/ def instead.

```python
triple = lambda x: x * 3
add = lambda x, y: x + y
print(add(triple(3), 4))
#this will output 13
```