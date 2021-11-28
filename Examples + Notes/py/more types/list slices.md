list slices provide a more advanced way of retrieving values from a list. basic list slicing involves indexing a list w/ two colon-separated integers. This returns a new list containing all of the values in the old list btwn the indices

```python
squares = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
print(squares[2:6])
print(squares[3:8])
print(squares[0:1])
```

like the arguments to range, first index provided in a slice is included in the result, but the second isn't

```python
#i.e.
sqs = [0, 1, 4, 9, 16, 25, 36, 49, 64]
print(sqs[4:7])

>>>[16, 25, 36]
#the list does not include the last item stated in list slice
```

if the first number of slice is omitted, it is taken to the start of the list. If the second number is omitted, it is taken to the end.

```python
squares = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
print(squares[:7])
print(squares[7:])
```

note: slicing can also be done on tuples

```python
#i.e.
list = ["a", "b", "c", "d"]
a = list[0:2]
print(a)

>>>first 2 elements of list
```

list slices can also have a third value, representing the step, to include only alternate values in the slice

```python
squares = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
print(squares[::2])
print(squares[2:8:3])

>>>#[2:8:3] will include elements starting from the 2nd index up to the 8th with a step of 3
```

```python
#i.e.
sqs = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
print(sqs[1::4])

>>>[1, 25, 81]
```

negative values can be used in list slicing & normal list indexing. When negative values are used for the 1st and 2nd values in a slice(or a normal index), they count from the end of the list

```python
squares = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
print(squares[1:-1])
```

note: if a negative value is used for the step, the slice is done backwards. Using \[::-1\] as a slice is a common and idiomatic way to reverse a list

```python
#i.e.
sqs = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
print(sqs[7:5:-1])

>>>[49, 36]
```