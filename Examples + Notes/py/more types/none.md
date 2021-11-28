```py
#none value used to represent absence of a value
#similar to null in other programming languages(like Java)

#like other "empty" values, like 0, [], and the empty string(""), it is False when converted to a bool variable
#when entered @ the python console, it is displayed as the empty string

>>> None == None
True

>>> None
>>> print(None)
None
>>>
```

```py
#none object is returned by any function that doesn't explicitly return anything else.
def some_func():
	print("Hi!")

var = some_func()
print(var)
```

```py
foo = print()
if foo == None:
   print(1)
else:
   print(2)

#i.e. in this case, code prints 1 since there is no value in the variable
```