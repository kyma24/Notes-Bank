# Tip 1
# converting a string of letters into a list
```python
s = "ABCDEFG"
w = [i for i in s]
```

# Tip 2.1
# print numbers in a list in space delimited line
```python
n = [1, 2, 3, 4, 5, 6]
print (" ".join(list(map(str, n))))
```

# print numbers in a list in one line with # as the delimiter
# such as 1#2#3#4#5#6
```python
n = [1, 2, 3, 4, 5, 6]
print ("#".join(list(map(str, n))))
```

# Tip 2.2
# print words in a list in space dilimted line
```python
a = ["Apple", "Banana", "Kiwi", "Orange", "Pear"]
print (" ".join(a))
```

# Tip 3
# Find indices of items in a list using enumerate
```python
s = "ABCDEFGABCDEFG"
w = [i for i in s]
print (list(enumerate(w)))
for i in "ABCDEFG":
index = [ind for ind, e in enumerate(w) if e == i]
print (" ".join(list(map(str, index))))
```

# Tip 4
# Reversing a list using slicing technique
```python
rev_lst = lst[::-1]
```

# Tip 5
# Combinations
# A Python program to print all
# combinations of given length
from itertools import combinations

# Get all combinations of [1, 2, 3]
# and length 2
comb = combinations([1, 2, 3], 2)

# Print the obtained combinations
for i in list(comb):
print (i)

# Tip 6
# Permuations
# A Python program to print all
# permutations of given length
from itertools import permutations

# Get all permutations of length 2
# and length 2
perm = permutations([1, 2, 3], 2)

# Print the obtained permutations
for i in list(perm):