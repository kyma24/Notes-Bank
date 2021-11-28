so far, to combine strings & non-strings, the non-strings have been converted to strings and concatenated them.

string formatting provides a more powerful way to embed non-strings within strings. String formatting uses a string's format method to substituted a number of arguments in the string

```python
#string formatting
nums = [4, 5, 6]
msg = "Numbers: {0} {1} {2}". format(nums[0], nums[1], nums[2])
print(msg) 
```

each argument of the format function is placed in the string at the corresponding position, which is determined using the curly braces{}

```python
#i.e.
print("{0}{1}{0}".format("abra", "cad")

>>>abracadabra
```

string formatting can also be done w/ named arguments

```python
a = "{x}, {y}".format(x=5, y=12)
print(a)
```

```python
#i.e.
str = "{c}, {b}, {a}".format(a=5, b=9, c=7)
print(str)

>>>7, 9, 5
```