sets are data structures, similar to lists/dictionaries. They are created using curly brackets, or the set function. They share some functionality with lists, such as the use of in to check whether they contain a particular item.

```python
num_set = {1, 2, 3, 4, 5}
word_set = set(["spam", "eggs", "sausage"])

print(3 in num_set)
print("spam" not in word_set)
```

to create an empty set, you must use set(), as {} creates an empty dictionary

sets differ from lists in several ways, but share several list operations such as len.

-   they are **unordered**, which means that they can't be indexed.
-   they can't contain duplicate elements.
-   due to the way they are stored, it's **faster** to check whether an item is part of a set, rather than part of a list
-   instead of using **append** to add to a set, use **add**
-   the method **remove** removes a specific element from a set; **pop** removes a arbitrary element.

```python
nums = {1, 2, 1, 3, 1, 4, 5, 6}
print(nums)
nums.add(-7)
nums.remove(3)
print(nums)
```

basic uses of sets include membership testing & the elimination of duplicate entries.

sets can be combined using mathematical operations.

the **union** operator **|** combines 2 sets to form a new one containing items in either(or)

the **intersection** operator **&** gets items in only both. (and)

the **difference** operator **\-** gets items in the first set but not in the second.

the **symmetric difference** operator **^** gets items in either set, but not both

```python
first = {1, 2, 3, 4, 5, 6}
second = {4, 5, 6, 7, 8, 9}

print(first | second)
print(first & second)
print(first - second)
print(second - first)
print(first ^ second)
```