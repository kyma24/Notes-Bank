generators are a type of iterable, like lists or tuples.

unlike lists, they don't allow indexing w/ arbitrary indices, but they can still be iterated through with for loops.

They can be created using functions and the **yield** statement.

```python
def countdown():
	i = 5
	while i > 0:
		yield i
		i -= 1

for i in countdown():
	print(i)
```

The yield statement is used to define a generator, replacing the return of a function to provide a result to its caller without destroying local variables.

and due to the fact that they yield one item at a time, generators don't have the memory restrictions of lists(they can be infinite)

```python
def infinite_sevens():
	while True:
		yield 7

for i in infinite_sevens():
	print(i)

#result: infinite sevens(7 7 7 7 7 7...)
```

in short, generators allow you to declare a function that behaves like an iterator, i.e. it can be used in a for loop.

finite generators can be converted into lists by passing them as arguments to the list function

```python
def numbers(x):
	for i in range(x):
		 if i % 2 == 0:
				yield i

print(list(numbers(11))
```

using generators results in improved performance, which is the result of the lazy/on demand generation of values, which translates to lower memory usage. Furthermore, we don't need to wait until all the elements have been generated before we start to use them.

```python
def make_word():
  word = ""
  for ch in "spam":
    word +=ch
    yield word

print(list(make_word()))

#prints ['s', 'sp', 'spa', 'spam']
```