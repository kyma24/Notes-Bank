-   data structures used to map arbitrary keys to values
-   lists can be thought of as dictionaries with integer keys within a certain range
-   dictionaries can be indexed in same way as lists, using **square brackets** containing keys

```py
ages = {"Dave": 24, "Mary": 42, "John": 58}
print(ages["Dave"])
print(ages["Mary"])
```

note: each element in a dictionary is represented by a **key: value** pair

-   trying to index a key that isn't part of the dictionary returns a **KeyError**
```py
#i.e.
primary = {
	"red": [255, 0, 0],
	"green": [0, 255, 0],
	"blue": [0, 0, 255]
}

print(primary["red"])
print(primary["yellow"])
```

note: dictionary can store any types of data as values. An empty dictionary is defined as {}

-   only immutable objects can be used as keys to dictionaries. **Immutable objects** are those that can't be changed. Lists and dictionaries are mutable. Trying to use a mutable object as a dictionary key causes a TypeError

```python
#i.e.
bad_dict = {
	[1, 2, 3]: "one two three",
}
```



like lists, dictionary keys can be assigned to different values

-   unlike lists, new dictionary key can also be assigned a value, not just ones that already exist

```python
squares = {1: 1, 2: 4, 3: "error", 4: 16,}
squares[8] = 64
squares[3] = 9
print(squares)
```

to determine whether a key is in a dictionary, you can use **in** and **not in**, just as you can for a list

```python
nums= {
	1: "one",
	2: "two",
	3: "three",
}
print(1 in nums)
print("three" in nums)
print(4 not in nums)
```

a useful dictionary method is **get**. it does the same as indexing, but if the key isn't found in the dictionary it returns another specified value instead(none by default)

```python
pairs = {
	1: "apple",
	"orange": [2, 3, 4],
	True: False,
	None: "True",
}

print(pairs.get("orange"))
print(pairs.get(7))
print(pairs.get(12345, "not in dictionary"))
```

```python
fib = {1: 1, 2: 1, 3: 2, 4: 3}
print(fib.get(4, 0) + fib.get(7, 5))
#returns (3 + 5) = 8
```

two parameters of the get method:

_dictionary_.get(_keyname_, _value_)

_keyname_: required. keyname of item you want to return the value from

_value_: optional. a value to return if the specified key doesn't exist. Default value is none.