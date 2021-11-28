useful way of quickly creating lists whose contents obey a simple rule

```python
#i.e.
cubes = [i**3 for i in range(5)]

print(cubes)
```

these are inspired by set-builder notation in math

a list comprehension can also contain an if statement to enforce a condition on values in the list

```python
evens=[i**2 for i in range(10) if i**2 % 2 == 0]

print(evens)
```

trying to create a list in a very extensive range will result in **MemoryError**. This code shows an example where the list comprehension runs out of memory

```python
even = [2*1 for i in range(10**100)]
```