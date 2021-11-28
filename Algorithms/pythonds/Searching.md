### Searching
Searching and sorting problems are probably the most common problems that arise in computing. Searching is the algorithmic process of finding a particular item in a collection of items. A search typically answers either `True` or `False` as to whether the item is present. On occasion it may be modified to return where the item is found. For our purposes here, we'll simple concern ourselves with the questino of membership.

In Python, there's a very easy way to ask whether an item is in a list of items. We use the `in` operator.
```python
>>> 15 in [3,5,2,4,1]
False
>>> 3 in [3,5,2,4,1]
True
>>>
```

Even though this is easy to write, an underlying process must be carried out to answer the question. It turns out that there are many different ways to search for the item. What we're interested here is how these algorithms work and how they compare to one another.

### The Sequential Search
When data items are stored in a collection such as a list, we say that they have a linear or sequential relationship. Each data item is stored in a position relative to the others. In python lists, these relative positions are the index values of the individual items. Since these index values are ordered, it's possible for us to visit them in sequence. This process gives rise to the first searching technique, the **sequential search**.

The figure below shows how this search works. Starting at the first term in the list, we simply move from item to item, following the underlying sequential ordering until we either find what we're looking for or run out of items. If we run out of items, we have discovered that the item we were searching for wasn't present.
![[Sequential Search of a List of Integers.png]]

The Python implementation for this algorithm is shown below. The function needs the list and the item we are looking for and returns a boolean value as to whether it's present. The boolean variable `found` is initialized to `False` and is assigned the value `True` if we discover the item in the list.
```python
def sequentialSearch(alist,item):
	pos = 0
	found = False
	
	while pos < len(alist) and not found:
		if alist[pos] == item:
			found = True
		else:
			pos = pos + 1
			
	return found

testlist = [1, 2, 32, 8, 17, 19, 42, 13, 0]
print(sequentialSearch(testlist, 3))
print(sequentialSearch(testlist, 13))
```

### Analysis of Sequential Search
To analyze searching algorithms, we need to decide on a basic unit of computations. Recall that this is typically the common step that must be repeated in order to solve the problem. For searching, it makes sense to count the number of comparisons performed. Each comparison may or may not discover the item we are looking for. In addition, we make another assumption here; the list of items isn't ordered in any way. The items have been placed randomly into the list. In other words, the probability that the item we are looking for is in any particular position is exactly the same for each position of the list.

If the item isn't in the list, the only way to know it is to compare it against every item present. If there are ${n}$ items, then the sequential search requires ${n}$ comparisons to discover that the item isn't here. In the case where the item is in the list, the analysis isn't so straightforward. There are actually three different scenarios that can occur. In the best case we'll find the item in the first place we look, at the beginning of the list. We'll need only one comparison. In the worst case, we won't discover the item until the very last comparison, the *nth* comparison.

What about the average case? On average, we'll find the item abt halfway into the list; that is, we'll compare against ${\frac{n}{2}}$ items. Recall, however, that as *n* gets large, the coefficients, no matter what they are, become insignificant in the approximation, so the complexity of the sequential search is, ${O(n)}$. The table below summarizes these results.

case | best case | worst case | average case
-----|-----------|----------|--------------
item is present | ${1}$ | ${n}$ | ${\frac{n}{2}}$
item is not present | ${n}$ | ${n}$ | ${n}$

We assumed earlier that the items in the collection had been randomly placed so that there is no relative order between the items. What would happen to the sequential search if the items were ordered in some way? Would we be able to gain any efficiency in the search technique?

Assume that the list of items was constructed so that the items were in ascending order, from low to high. If the item we're looking for is present in the list, the chances of it being in any one of the *n* positions is still the same as before. We'll still have the same number of comparisons to find the item. However, if the item isn't present there's a slight advantage. Below shows the process as the algorithm looks for the item 50. Notice that items are still compared in sequence until 54. At this point, however, we know something extra; not only is 54 not the item we're looking for, but no other elements beyond 54 can work either since the list is sorted. In this case, the algorithm doesn't have to continue looking through all of the items to report that the item wasn't found. It can stop immediately. The code below shows this variation of the sequential search function.
![[Sequential Search of an Ordered List of Integers.png]]

```python
def orderedSequentialSearch(alist,item):
	pos = 0
	found = False
	stop = False
	while pos < len(alist) and not found and not stop:
		if alist[pos] == item:
			found = True
		else:
			if alist[pos] > item:
				stop = True
			else:
				pos = pos + 1
				
	return found
	
testlist = [0, 1, 2, 8, 13, 17, 19, 32, 42,]
print(orderedSequentialSearch(testlist, 3))
print(orderedSequentialSearch(testlist, 13))
```

The table below summarizes these results. Note that in the best case we might discover that the item isn't in the list by looking at only one item. On average, we will know after looking through only ${\frac{n}{2}}$ items. However, this technique is still ${O(n)}$. In summary, a sequential search is improved by ordering the list only in the case where we don't find the item.

Comparisons Used in Sequential Search of an Ordered List

 |  |  | 
 -----------------|--------|---------|--------------
 item is present | ${1}$ | ${n}$ | ${\frac{n}{2}}$
 item not present  | ${1}$ | ${n}$ | ${\frac{n}{2}}$
 
 ### The Binary Search
 It's possible to take greater advantage of the ordered list if we are clever w/ our comparisons. In the sequential search, when we compare against the first term, there are at most ${n-1}$ more items to look through if the first item isn't what we're looking for. Instead of searching the list in sequence, a **binary search** will start by examining the middle item. If that item is the one we're searching for, we are done. If it is not the correct item, we can use the ordered nature of the list to eliminate half of the remaining items. If the item we are searching for is greater than the middle item, we know that the entire lower half of the list as well as the middle item can be eliminated from further consideration. The item, if it is in the list, must be in the upper half.
 
 We can then repeat the process with the upper half. Start at the middle item and compare it against what we are looking for. Again, we either find it or split the list in half, therefore eliminating another large part of our possible search space. The figure below shows how this algorithm can quickly find the value 54. The complete function is shown in the code below.
![[Binary Search of an Ordered List of Integers.png]]
 
 ```python
 def binarySearch(alist,item):
 	first = 0
	last = len(alist)-1
	found = False
	
	while first <= last and not found:
		midpoint = (first+last)//2
		if alist[midpoint] == item:
			found = True
		else:
			if item < alist[midpoint]:
				last = midpoint-1
			else:
				first = midpoint+1
	return found
	
testlist = [0, 1, 2, 8, 13, 17, 19, 32, 42,]
print(binarySearch(testlist,3))
print(binarySearch(testlist,13))
```

Before we move on to the analysis, we should note that this algorithm is a greate example of a divide and conquer strategy. Divide and conquer means that we divide the problem into smaller pieces, solve the smaller pieces in some way, and then reassemble the whole problem to get the result. When we perform a binary search of a list, we first check the middle item. If the item we are searching for is less than the middle item, we can simply perform a binary search of the left half of the original list. Likewise, if the item is greater, we can perform a binary search of the right half. Either way, this is a recursive call to the binary search function passing a smaller list. Below shows this recursive version.
```python
def binarySearch(alist,item):
	if len(alist) == 0:
		return False
	else:
		midpoint = len(alist)//2
		if alist[midpoint] == item:
			return True
		else:
			if item < alist[midpoint]:
				return binarySearch(alist[:midpoint],item)
			else:
				return binarySearch(alist[midpoint+1:], item)
testlist = [0, 1, 2, 8, 13, 17, 19, 32, 42,]
print(binarySearch(testlist,3))
print(binarySearch(testlist,13))
```

### Analysis of Binary Search
To analyze the binary search algorithm, weneed to recall that each comparison eliminates about half of the remaining items from consideration. What is the maximum number of comparisons this algorithm will require to check the entire list? If we start with *n*  items, about ${\frac{n}{2}}$ items will be left after the first comparison. After the second comparison, there will be about ${\frac{n}{4}}$. Then ${\frac{n}{8}}$, ${\frac{n}{16}}$, and so on. How many times can we split the list? The table below helps us to see the answer.

Tabular Analysis for a Binary Search

Comparisons | Approximate Number of Items Left
-------------------|-------------------------
1 | ${\frac{n}{2}}$
2 | ${\frac{n}{4}}$
3 | ${\frac{n}{8}}$
... | 
i | ${\frac{n}{2^{i}}}$

When we split the list enough times, we end up with a list that has just one item. Either that is the item we are looking for or it is not. Either way, we're done. The number of comparisons necessary to get to this point is *i* where ${\frac{n}{2^{i}} = 1}$. Solving for *i* gives us ${i = log\hspace{0.2cm}n}$. The maximum number of comparisons is logarithmic with respect to the number of items in the list. Therefore, the binary search is ${O(log\hspace{0.2cm}n)}$.

One additional analysis issue needs to be addressed. In the recursive solution shown above, the recursive call,
`binarySearch(alist[:midpoint],item)`
uses the slice operator to create the left half of the list that is then passed to the next invocation(similarly for the right half as well). The analysis that we did above assumed that the slice operator in Python is actually O(k). This means that the binary search using slice won't perform in strict logarithmic time. Luckily this can be remedied by passing the list along with the starting and ending indices. The indices can be calculated as we did in the code.

Even though a binary search is generally better than a sequential search, it is important to note that for small values of *n*, the additional cost of sorting is probably not worth it. In fact, we should always consider whether it is cost effective to take on the extra work of sorting to gain searching benefits. If we can sort once and then search many times, the cost of the sort is not so significant. However, for large lists, sorting even once can be so expensive that simply performing a sequential search from the start may be the best choice.

### Hashing
In the previous sections we were able to make improvements in the search algorithms by taking advantage of information about where items are stored in the collection w/ respect to one another. For example, by knowing that a list was ordered, we could search in logarithmic time using a binary search. In this section we'll attempt to go one step further by building a data structure that can be searched in ${O(1)}$ time. This concept is referred to as **hashing**.

In order to do this, we'll need to know even more abt where the items might be when we go to look for them in the collection. If every item is where it should be, then the search can use a single comparison to discover the presence of an item. We'll see, however, that this is typically not the case.

A **hash table** is a collection of items which are stored in such a way as to make it easy to find them later. Each position of the hash table, often called a **slot**, can hold an item and is named by an integer value starting at 0. For example, we'll have a slot named 0, a slot named 1, a slot named 2, and so on. Initially, the hash table contains no items so every slot is empty. We can implement a hash table by using a list with each element initialized to the special Python value `None`. Below is a hash table of size ${m = 11}$. In other words, there are *m* slots in the table, named 0 through 10.
![[Hash Table with 11 Empty Slots.png]]

The mapping between an item and the slot where that item belongs in the hash table is called the **hash function**. The hash function will take any item in the collection and return an integer in the range of slot names, between 0 and m-1. Assume that we have the set of integer items 54, 26, 93, 17, 77, and 31. Our first hash function, sometimes referred to as the "remainder method", simply takes an item and divides it by the table size, returning the remainder as its hash value (${h(item) = item\%11}$). The table below gives all of the hash values for the example items. Note that this remainder method(modulo arithmetic) will typically be present in some form in all hash functions, since the result must be in range of slot names.

Item | Hash Value
--------|----------
54 | 10
26 | 4
93 | 5
17 | 6
77 | 0
31 | 9

Once the hash values have been computed, we can insert each item into the hash table at the designated position as shown below. Note that 6 of the 11 slots are now occupied. This is referred to as the **load factor**, and is commonly denoted by ${λ=\frac{numberofitems}{tablesize}}$. For this example, ${λ=\frac{6}{11}}$.
![[Hash Table with Six Items.png]]

Now when we want to search for an item, we simply use the hash function to compute the slot name for the item and then check the hash table to see if it's present. This searching operation is ${O(1)}$, since a constant amount of time is required to compute the hash value and then index the hash table at that location. If everything is where it should be, we have found a constant time search algorithm.

You can probably already see that this technique is going to work only if each item maps to a unique location in the hash table. For example, if the item 44 had been the next item in our collection, it would have a hash value of 0 (${44\%11==0}$). Since 77 also had a hash value of 0, we would have a problem. According to the hash function, two or more items would need to be in the same slot. This is referred to as a **collision**(may also be called a "clash"). Clearly, collisions create a problem for the hashing technique.

### Hash Functions
Given a collection of items, a hash function that maps each item into a unique slot is referred to as a **perfect hash function**. If we know the items and the collection will never change, then it's possible to construct a perfect hash function. Unfortunately, given an arbitrary collection of items, there is no systematic way to construct a perfect hash function. Luckily, we don't need the hash function to be perfect to still gain performance efficiency.

One way to always have a perfect hash function is to increase the size of the hash table so that each possible value in the item range can be accommodated. This guarantees that each item will have a unique slot. Although this is practical for small numbers of items, it isn't feasible when the number of possible items is large. For example, if the items were 9-digits Social Security numbers, this method would require almost one billion slots. If we only want to store data for a class of 25 students, we'll be wasting an enormous amount of memory.

Our goal is to create a hash function that minimizes the number of collisions, is easy to compute, and evenly distributes the items in the hash table. There are a number of common ways to extend the simple remainder method. We'll consider a few of them here.

The **folding method** for constructing hash functions begins by dividing the item into equal-size pieces(the last piece may not be of equal size). These pieces are then added together to give the resulting hash value. For example, if the item was the phone number 436-555-4601, we would take the digits and divide them into groups of 2(43,65,55,46,01). After the addition, ${43 + 65 + 55 + 46 + 01}$, we get 210. If we assume our hash table has 11 slots, then we need to perform the extra step of dividing by 11 and keeping the remainder. In this case ${210 \% 11}$ is 1, so the phone number 436-555-4601 hashes to slot 1. Some folding methods go one step further and reverse every other piece before the addition. For the above example, we get ${43 + 56 + 55 + 64 + 01}$ = 219 which gives ${210 \% 11 = 10}$.

Another numerical technique for constructing a hash function is called the **mid-square method**. We first square the item, and then extract some portion of the resulting digits. For example, if the item were 44, we would first compute ${44^{2} = 1,936}$. By extracting the middle two digits, 93, and performing the remainder step, we get 5 (${93 \% 11}$). The table below shows items under both the remainder method and the mid-square method.

Item | Remainder | Mid-Square
-------|----------|-----------
54 | 10 | 3
26 | 4 | 7
93 | 5 | 9
17 | 6 | 8
77 | 0 | 4
31 | 9 | 6

We can also create hash functions for character-based items such as strings. The word "cat" can be thought of as a sequence of ordinal values.
```python
>>> ord('c')
99
>>> ord('a')
97
>>> ord('t')
116
```

We can then take these three ordinal values, add them up, and use the remainder method to get a hash value. The code below shows a function called `hash` that takes a string and a table size and returns the hash value in the range from 0 to `tablesize`-1.
![[Hashing a String Using Ordinal Values.png]]

```python
def hash(astring, tablesize):
	sum = 0
	for pos in range(len(astring)):
		sum = sum + ord(astring[pos])
		
	return sum%tablesize
```

It's interesting to note that when using this hash function, anagrams will always be given the same hash value. To remedy this, we could use the position of the character as a weight. The figure below shows one possible way to use the positional value as a weighting factor.
![[Hashing a String Using Ordinal Values with Weighting.png]]

You may be able to think of a number of additional ways to compute hash values for items in a collection. The important thing to remember is that the hash function has to be efficient so that it doesn't become the dominant part of the storage and search process. If the hash function is too complex, then it becomes more work to compute the slot name than it would be to simply do a basic sequential or binary search as described earlier. This would quickly defeat the purpose of hashing.

### Collision Resolution
We now return to the problem of collisions. When two items hash to the same slot, we must have a systematic method for placing the second item in the hash table. This process is called **collision resolution**. As stated earlier, if the hash function is perfect, collisions will never occur. However, since this is often not possible, collision resolution becomes a very important part of hashing.

One method of resolving collisions looks into the hash table and tries to find another open slot to hold the item that caused the collision. A simple way to do this is to start at the original hash value position and then move in a sequential manner through the slots until we encounter the first slot that is empty. Note that we may need to go back to the first slot(circularly) to cover the entire hash table. The collision resolution process is referred to as **open addressing** in that it tries to find the next open slot or address in the hash table. By systematically visiting each slot one at a time, we are performing an open addressing technique called **linear probing**.

The figure below shows an extended set of integer items under the simple remainder method hash function (54, 26, 93, 17, 77, 31, 44, 55, 20). The table of simple hash function using remainders above shows the hash values for the original items. The figure underneath the said table shows the original contents. When we attempt to place 44 into slot 0, a collision occurs. Under linear probing, we look sequentially, slot by slot, until we find an open position. In this case, we find slot 1.

Again, 55 should go in slot 0 but must be placed in slot 2 since it's the next open position. The final value of 20 hashes to slot 9. Since slot 9 is full, we begin to do linear probing. We visit slots 10, 0, 1, and 2, and finally find an empty slot at position 3.
![[Collision Resolution with Linear Probing.png]]

Once we have built a hash table using open addressing and linear probing, it's essential that we utilize the same methods to search for items. Assume we want to look up the item 93. When we compute the hash value, we get 5. Looking in slot 5 reveals 93, and we can return `True`. What if we're looking for 20? Now the hash value is 9, and slot 9 is currently holding 31. We can't simply return `False` since we know that there could have been collisions. We are now forced to do a sequential search, starting at position 10, looking until we either find the item 20 or we find an empty slot.

A disadvantage to linear probing is the tendency for **clustering**; items become clustered in the table. This means that if many collisions occur at the same hash value, a number of surrounding slots will be filled by the linear probing resolution. This will have an impact on other items that are being inserted, as we saw when we tried to add the item 20 above. A cluster of values hashing to 0 had to be skipped to finally find an open position. This cluster is shown below.
![[A Cluster of Items for Slot 0.png]]

One way to deal with clustering is to extend the linear probing technique so that instead of looking sequentially for the next open slot, we skip slots, thereby more evenly distributing the items that have caused collisions. This will potentially reduce the clustering that occurs. The figure below shows the items when collision resolution is done with a "plus 3" probe. This means that once a collision occurs, we'll look at every third slot until we find one that is empty.
![[Collision Resolution Using “Plus 3”.png]]

The general name for this process of looking for another slot after a collision is **rehashing**. With simple linear probing, the rehash function is ${newhashvalue = rehash(oldhashvalue)}$ where ${rehash(pos) = (pos+1)\%sizeoftable}$. The "plus 3" rehash can be defined as ${rehash(pos) = (pos+3)\%sizeoftable}$. In general, ${rehash(pos) = (pos.skip)\%sizeoftable}$. It is important to note that the size of the "skip" must be such that all the slots in the table will eventually be visited. Otherwise, part of the table will be unused. To ensure this, it is often suggested that the table size be a prime number. This is the reason we have been using 11 in the examples.

A variation of the linear probing idea is called **quadratic probing**. Instead of using a constant "skip" value, we use a rehash function that increments the hash value by 1, 3, 5, 7, 9, and so on. This means that if the first hash value is *h*, the successive values are ${h+1}$, ${h+4}$, ${h+9}$, ${h+16}$, and so on. In general, the i will be i^2 ${rehash(pos) = (h+i^{2})}$. In other words, quadratic probing uses a skip consisting of successive perfect squares. The figure below shows the example values after they are placed using this technique.
![[Collision Resolution with Quadratic Probing.png]]

An alternative method for handling the collision problem is to allow each slot to hold a reference to a collection(or chain) of items. **Chaining** allows many items to exist at the same location in the hash table. When collisions happen, the item is still placed in the proper slot of the hash table. As more and more items hash to the same location, the difficulty of searching for the item in the collection increases. The figure below shows the items as they were added to the hash table that uses chaining to resolve collisions.
![[Collision Resolution with Chaining.png]]

When we want to search for an item, we use the hash function to generate the slot where it should reside. Since each slot holds a collection, we use a searching technique to decide whether the item is present. The advantage is that on the average there are likely to be many fewer items in each slot, so the search is perhaps more efficient. We'll look at the analysis for hashing at the end of this section.

### Implementing the `Map` Abstract Data Type
One of the most useful Python collections is the dictionary. Recall that a dictionary is an associative data type where you can store key-data pairs. The key is used to look up the associated data value. We often refer to this idea as a **map**.

The map abstract data type is defined as follows. The structure is an unordered collection of associations between a key and a data value. The keys in a map are all unique so that there is a one-to-one relationship between a key and a value. The operations are given below.

- `Map()` creates a new, empty map. It returns an empty map collection.
- `put(key,val)` adds a new key-value pair to the map. If the key is already in the map then replace the old value with the new value.
- `get(key)` given a key, return the value stored in the map or `None` otherwise
- `del` deletes the key-value pair frojm the map using the statement of the form `del map[key]`
- `len()` returns the number of key-value pairs stored in the map
- `in` returns `True` for a statement of the form `key in map`, if the given key is in the map, `False` otherwise.

One of the great benefits of a dictionary is the fact that given a key, we can look up the associated data value very quickly. In order to provide this fast look up capability, we need an implementation that supports an efficient search. We could use a list with sequential or binary search but it would be even better to use a hash table as described above since looking up an item in a hash table can approach ${O(1)}$ performance.

In the code below we use two lists to create a `HashTable` class that implements the Map abstract data type. One list, called `slots`, will hold the key items and a parallel list, called `data`, will hold the data values. When we look up a key, the corresponding position in the data list will hold the associated data value. We will treat the key list as a hash table using the ideas presented earlier. Note that the initial size for the hash table has been chosen to be 11. Although this is arbitrary, it is important that the size be a prime number so that the collision resolution algorithm can be as efficient as possible.
```python
class HashTable:
	def __init__(self):
		self.size = 11
		self.slots = [None] * self.size
		self.data = [None] * self.size
```

`hashfunction` implements the simple remainder method. The collision resolution technique is linear probing with a "plus 1" rehash function. The `put` function(see below) assumes that there will eventually be an empty slot unless the key is already present in the `self.slots`. It computes the original hash value and if that slot isn't empty, iterates the `rehash` function until an empty slot occurs. If a nonempty slot already contains the key, the old data value is replaced with the new data value. (deal w/ the situation where there are no empty slots: ==exercise==)

```python
def put(self,key,data):
  hashvalue = self.hashfunction(key,len(self.slots))

  if self.slots[hashvalue] == None:
    self.slots[hashvalue] = key
    self.data[hashvalue] = data
  else:
    if self.slots[hashvalue] == key:
      self.data[hashvalue] = data  #replace
    else:
      nextslot = self.rehash(hashvalue,len(self.slots))
      while self.slots[nextslot] != None and \
                      self.slots[nextslot] != key:
        nextslot = self.rehash(nextslot,len(self.slots))

      if self.slots[nextslot] == None:
        self.slots[nextslot]=key
        self.data[nextslot]=data
      else:
        self.data[nextslot] = data #replace

def hashfunction(self,key,size):
     return key%size

def rehash(self,oldhash,size):
    return (oldhash+1)%size
```

Likewise, the `get` function(see code below) begins by computing the initial hash value. If the value isn't in the initial slot, rehash is used to locate the next possible position. Notice that the 15th line guarantees that the search will terminate by checking to make sure that we have not returned to the initial slot. if that happens, we have exhausted all possible slots and the item must not be present.

The final methods of the `HashTable` class provide additional dictionary functionality. We overload the \_\_getitem\_\_ and \_\_setitem\_\_ methods to allow access using "\[\]". This means that once a `HashTable` has been created, the familiar index operator will be available.(rest of methods left as ==exercise==)
```python
def get(self,key):
  startslot = self.hashfunction(key,len(self.slots))

  data = None
  stop = False
  found = False
  position = startslot
  while self.slots[position] != None and  \
                       not found and not stop:
     if self.slots[position] == key:
       found = True
       data = self.data[position]
     else:
       position=self.rehash(position,len(self.slots))
       if position == startslot:
           stop = True
  return data

def __getitem__(self,key):
    return self.get(key)

def __setitem__(self,key,data):
    self.put(key,data)
```

The following session shows the `HashTable` class in action. First, we'll create a hash table and score some items with integer keys and string data values.
```python
>>> H=HashTable()
>>> H[54]="cat"
>>> H[26]="dog"
>>> H[93]="lion"
>>> H[17]="tiger"
>>> H[77]="bird"
>>> H[31]="cow"
>>> H[44]="goat"
>>> H[55]="pig"
>>> H[20]="chicken"
>>> H.slots
[77, 44, 55, 20, 26, 93, 17, None, None, 31, 54]
>>> H.data
['bird', 'goat', 'pig', 'chicken', 'dog', 'lion', 'tiger', None, None, 'cow', 'cat']
```

Next, we'll access + modify some items in the hash table. Note the value for the key 20 is being replaced.
```python
>>> H[20]
'chicken'
>>> H[17]
'tiger'
>>> H[20]='duck'
>>> H[20]
'duck'
>>> H.data
['bird', 'goat', 'pig', 'duck', 'dog', 'lion', 'tiger', None, None, 'cow', 'cat']
>>> print(H[99])
None
```

### Analysis of Hashing
As stated earlier, in the best case hashing would provide a ${O(1)}$, constant time search technique. However, due to collisions, the number of comparisons is typically not so simple. Even though a complete analysis of hashing is beyond the scope of this text, we can state some well-known results that approximate the number of comparisons necessary to search for an item.

The most important piece of information we need to analyze the use o a hash table is the load factor, λ. Conceptually, if λ is small, then there is a lower chance of collisions, meaning that items are more likely to be in the slots where they belong. If λ is large, meaning that the table is filling up, then there are more and more collisions. This means that collision resolution is more difficult, requiring more comparisons to find an empty slot. With chaining, increased collisions means an increased number of items on each chain.

As before, we'll have a result for both a successful and unsuccessful search. For a successful search using open addressing with linear probing, the average number of comparisons is approximately ${\frac{1}{2}(1 + \frac{1}{1-λ})}$ and an  unsuccessful search gives ${\frac{1}{2}(1+(\frac{1}{1-λ})^{2})}$. If we are using chaining, the average number of comparisons is ${1 + \frac{λ}{2}}$ for the successful case, and simply ${λ}$ comparisons if the search is unsuccessful.