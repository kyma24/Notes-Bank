decorators provide a way to modify functions using other functions.

this is ideal when you need to extend the functionality of functions that you don't want to modify.

```python
def decor(func):
	def wrap():
		print("============")
		func()
		print("============")
	return wrap

def print_text():
	print("Hello world!")

decorated = decor(print_text)
decorated()

#we defined a function named **decor** that has a single parameter **func**. Inside **decor**, we defined a nested function named **wrap**. The **wrap** function will print a string, then call **func()**, and print another string. The **decor** function returns the **wrap** function as a result.

#we could say that the variable **decorated** is a decorated version of **print_text** - it's **print_text** plus something.

#In fact, if we wrote a useful decorator we might want to replace **print_text** with the decorated version altogether so we always have our "plus something" version of **print_text**
```

This is done by re-assigning the variable that contains our function:

```python
print_text = decor(print_text)
print_text()

#now print_text corresponds to the decorated version.
```

in the previous example, the function was decorated by replacing the variable containing the function with a wrapped version.

```python
def print_text():
	print("Hello world!")

print_text = decor(print_text)
```

this pattern can be used at any time, to wrap any function.

Python provides support to wrap a function in a decorator by prepending the function definition with a decorator name and the @ symbol.

If we are defining a function we can "decorate" it using the @ symbol like:

```python
@decor
def print_text():
	print("Hello world!")
```

this will have the same result as the above code.

note: a single function can have multiple decorators.

```python
my_func = my_dec(my_func)
#yields the same behavior as
@my_dec
```