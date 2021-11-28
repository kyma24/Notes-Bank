the module itertools is a standard library that contains several functions useful in functional programming.

one type of function it produces is infinite iterators.

-   the function **count** counts up infinitely from a value.
-   the function **cycle** infinitely iterates through an iterable(i.e. a list or string)
-   the function **repeat** repeats an object, either infinitely or for a specific number of times.

```python
#i.e.
from itertools import count

for i in count(3):
	print(i)
	if i >= 11:
		break
```

there are many functions in itertools that operate on iterables, in a similar way to map and filter.

-   **takewhile** - takes items from an iterable while a predicate function remains true
-   **chain** - combines several iterables into one long one
-   **accumulate** - returns a running total of values in an iterable

```python
#i.e.
from itertools import accumulate, takewhile

nums = list(accumulate(range(8)))
print(nums)
print(list(takewhile(lambda x: x <= 6, nums)))
```

there are also several combinatoric functions in itertool, such as product & permutation

these are used when you want to accomplish a task w/ all possible combinations of some items

```python
#i.e.
from itertools import product, permutations

letters = ("A", "B")
print(list(product(letters, range(2))))
print(list(permutations(letters)))
```

```python
from itertools import product
a = {1, 2}
print(len(list(product(range(3), a))))
#will print out 6
```