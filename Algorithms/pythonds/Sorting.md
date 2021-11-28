### Sorting
Sorting is the process of placing elements from a collection in some kind of order. For example, a list of words could be sorted alphabetically or by length. A list of cities could be sorted by population, by area, or by zip code. We've already seen a number of algorithms that were able to benefit from having a sorted list(recall the final anagram example and the binary search).

There are many sorting algorithms that have been developed and analyzed. This suggests that sorting is an important area of study in computer science. Sorting a large number of items can take a substantial amount of computing resources. Like searching, the efficiency of a sorting algorithm is related to the number of items being processed. For small collections, a complex sorting method may be more trouble than it is worth. The overhead may be too high. On the other hand, for larger collections, we want to take advantage of as many improvements as possible. This section will discuss several sorting techniques and compare them with respect to their running time.

Before getting into specific sorting algorithms, we should think about the operations that can be used to analyze a sorting process. First, it will be necessary to compare two values to see which is smaller(or larger). In order to sort a collection, it will be necessary to have some systematic way to compare values to see if they are out of order.  The total number of comparisons will be the most common way to measure a sort procedure. Second, when values aren't in the correct position with respect to one another, it may be necessary to exchange them. This exchange is a costly operation and the total number of exchanges will also be important for evaluating the overall efficiency of the algorithm.

### The Bubble Sort
The **bubble sort** makes multiple passes through a list. It compares adjacent items and exchanges those that are out of order. Each pass through the list places the next largest value in its proper place. In essence, each item "bubbles" up to the location where it belongs.

The figure below shows the first pass of a bubble sort. The shaded items are being compared to see if they are out of order. If there are *n* items in the list, then there are ${n - 1}$ pairs of items that need to be compared on the first pass. It is important to note that once the largest value in the list is part of a pair, it will continually be moved along until the pass is complete.
![[bubbleSort - The First Pass.png]]

At the start of the second pass, the largest value is now in place. There are ${n-1}$ items left to sort, meaning that there will be ${n-2}$ pairs. Since each pass places the next largest value in place, the total number of passes necessary will be ${n-1}$. After completing the ${n-1}$ passes, the smallest item must be in the correct position with no further processing required. The complete `bubbleSort` function takes the list as a parameter, and modifies it by exchanging items as necessary.

The exchange operation, sometimes called a "swap", is slightly different in Python than in most other programming languages. Typically, swapping two elements in a list requires a temporary storage location(an additional memory location). A code fragment such as
```python
temp = alist[i]
alist[i] = alist[j]
alist[j] = temp
```
will exchange the *ith* and *jth* items in the list. Without the temporary storage, one of the values would be overwritten.

In Python, it's possible to perform simultaneous assignment. The statement `a,b = b,a` will result in two assignment statements being done at the same time(see below). Using simultaneous assignment, the exchange operation can be done in one statement.

Lines 5-7 in the code below perform the exchange of the ${i}$ and ${(i+1)th}$ items using the three-step procedure described earlier. Note that we could also have used the simultaneous assignment to swap the items.
![[Exchanging Two Values in Python.png]]

```python
def bubbleSort(alist):
	for passnum in range(len(alist)-1, 0, -1):
		for i in range(passnum):
			if alist[i] > alist[i+1]:
				temp = alist[i]
				alist[i] = alist[i+1]
				alist[i+1] = temp
				
alist = [54, 26, 93, 17, 77, 31, 44, 55, 20]
bubbleSort(alist)
print(alist)
```

To analyze the bubble sort, we should note that regardless of how the items are arranged in the initial list, ${n-1}$ passes will be made to sort a list of size *n*. The table below shows the number of comparisons for each pass. The total number of comparisons is the sum of the first ${n-1}$ integers. Recall that the sum of the first *n* integers is ${\frac{1}{2}n^{2} + \frac{1}{2}n}$. The sum of the first ${n-1}$ integers is ${\frac{1}{2}n^{2} + \frac{1}{2}n - n}$, which is ${\frac{1}{2}n^{2} - \frac{1}{2}n}$. This is still ${O(n^{2})}$ comparisons. In the best case, if the list is already ordered, no exchanges will be made. however, in the worst case, every comparison will cause an exchange. On average, we exchange half of the time.

Pass | Comparisons
-----|--------------
1 | ${n-1}$
2 | ${n-2}$
3 | ${n-3}$
... | ...
${n-1}$ | ${1}$

A bubble sort is often considered the most inefficient sorting method since it must exchange items before the final location is known. These "wasted" exchange operations are very costly. However, because the bubble sort makes passes through the entire unsorted portion of the list, it has the capability to do something most sorting algorithms can't. In particular, if during a pass there are no exchanges, then we know that the list must be sorted. A bubble sort can be modified to stop early if it finds that the list has become sorted. This means that for lists that require just a few passes, a bubble sort may have an advantage in that it will recognize the sorted list and stop. The code below shows this modification, which is often referred to as the **short bubble**.
```python
def shortBubbleSort(alist):
	exchanges = True
	passnum = len(alist)-1
	while passnum > 0 and exchanges:
		exchanges = False
		for i in range(passnum):
			if alist[i] > alist[i+1]:
				exchanges = True
				temp = alist[i]
				alist[i] = alist[i+1]
				alist[i+1] = temp
		passnum = passnum-1

alist = [20,30,40,90,50,60,70,80,100,110]
shortBubbleSort(alist)
print(alist)
```

### The Selection Sort
The **selection sort** improves on the bubble sort by making only one exchange for every pass through the list. In order to do this, a selection sort looks for the largest value as it makes a pass and, after completing the pass, places it in the proper location. As with a bubble sort, after the first pass, the largest item is in the correct place. After the second pass, the next largest is in place. This process continues and requires ${n-1}$ passes to sort *n* items, since the final item must be in place after the ${(n-1)}$st pass.

The figure below shows the entire sorting process. On each pass, the largest remaining item is selected and then placed in its proper location. The first pass places 93, the second pass places 77, the third places 55, and so on. The function is shown in the code below.
![[selectionSort.png]]

```python
def selectionSort(alist):
   for fillslot in range(len(alist)-1,0,-1):
       positionOfMax=0
       for location in range(1,fillslot+1):
           if alist[location]>alist[positionOfMax]:
               positionOfMax = location

       temp = alist[fillslot]
       alist[fillslot] = alist[positionOfMax]
       alist[positionOfMax] = temp

alist = [54,26,93,17,77,31,44,55,20]
selectionSort(alist)
print(alist)
```

You may see that the selection sort makes the same number of comparisons as the bubble sort and is therefore also ${O(n^{2})}$. However, due to the reduction in the number of exchanges, the selection sort typically executes faster in benchmark studies. In fact, for the list provided, the bubble sort makes 20 exchanges, while the selection sort makes only 8.

### The Insertion Sort
The **insertion sort**, although still ${O(n^{2})}$, works in a slightly different way. It always maintains a sorted sublist in the lower positions of the list. Each new item is then "inserted" back into the previous sublist such that the sorted sublist is one item larger. The figure below shows the insertion sorting process. The shaded items represent the ordered sublists as the algorithm makes each pass.
![[Pasted image 20210624153409.png]]

We begin by assuming that a list with one item(position ${0}$) is already sorted. On each pass, one for each item 1 through ${n-1}$, the current item is checked against those in the already sorted sublist. As we look back into the already sorted sublist, we shift those items that are greater to the right. When we reach a smaller item or the end of the sublist, the current item can be inserted.

The figure below shows the fifth pass in detail. At this point in the algorithm, a sorted sublist of five items consisting of 17, 26, 54, 77, and 93 exists. We want to insert 31 back into the already sorted items. The first comparison against 93 causes 93 to be shifted to the right. 77 and 54 are also shifted. When the item 26 is encountered, the shifting process stops and 31 is placed in the open position. Now we have a sorted sublist of six items.
![[Pasted image 20210624153744.png]]

The implementation of `insertionSort`(the code below) shows that there are again ${n-1}$ passes to sort *n* items. The iteration starts at position 1 and moves through position ${n-1}$, as these are the items that need to be inserted back into the sorted sublists. The 8th line performs the shift operation that moves a value up one position in the list, making room behind it for the insertion. Remember that this isn't a complete exchange as was performed in the previous algorithms.

The maximum number of comparisons for an insertion sort is the sum of the first ${n-1}$ integers. Again, this is ${O(n^{2})}$. However, in the best case, only one comparison needs to be done on each pass. This would be the case for an already sorted list.

One note about shifting versus exchanging is also important. In general, a shift operation requires approximately a third of the processing work of an exchange since only one assignment is performed. In benchmark studies, insertion sort will show very good performance.
```python
def insertionSort(alist):
	for index in range(1,len(alist)):
		currentvalue = alist[index]
		position = index
		
		while position > 0 and alist[position-1] > currentvalue:
			alist[position] = alist[position-1]
			position = position - 1
			
		alist[position] = currentvalue
		
alist = [54,26,93,17,77,31,44,55,20]
insertionSort(alist)
print(alist)
```

### The Shell Sort
The **shell sort**, sometimes called the "diminishing increment sort", improves on the insertion sort by breaking the original list into a number of smaller sublists, each of which is sorted using an insertion sort. THe unique way that these sublists are chosen is the key to the shell sort. Instead of breaking the list into sublists of contiguous items, the shell sort uses an increment `i`, sometimes called the **gap**, to create a sublist by choosing all items that are `i` items apart.

This can be seen in the former figure below. This list has nine items. If we use an increment of three, there are three sublists, each of which can be sorted by an insertion sort. After completing these sorts, we get the list shown in the latter figure below. Although this list isn't completely sorted, something very interesting has happened. By sorting the sublists, we've moved the items closer to where they actually belong.
![[Pasted image 20210624162802.png]]
![[Pasted image 20210624162813.png]]

The figure below shows a final insertion sort using an increment of one; in other words, a standard insertion sort. Note that by performing the earlier sublist sorts, we have now reduced the total number of shifting operations necessary to put the list in its final order. For this case, we need only four more shifts to complete the process.
![[Pasted image 20210624162925.png]]

![[Pasted image 20210624163031.png]]

It was stated earlier that the way in which the increments are chosen is the unique feature of the shell sort. The function shown in the code below uses a different set of increments. In this case, we begin with ${\frac{n}{2}}$ sublists. On the next pass, ${\frac{n}{4}}$ sublists are sorted. Eventually, a single list is sorted with the basic insertion sort. The figure above shows the first sublists for the example using this increment.

The following invocation of the `shellSort`	function shows the partially sorted lists after each increment, with the final sort being an insertion sort with an increment of one.
```python
def shellSort(alist):
    sublistcount = len(alist)//2
    while sublistcount > 0:

      for startposition in range(sublistcount):
        gapInsertionSort(alist,startposition,sublistcount)

      print("After increments of size",sublistcount,
                                   "The list is",alist)

      sublistcount = sublistcount // 2

def gapInsertionSort(alist,start,gap):
    for i in range(start+gap,len(alist),gap):

        currentvalue = alist[i]
        position = i

        while position>=gap and alist[position-gap]>currentvalue:
            alist[position]=alist[position-gap]
            position = position-gap

        alist[position]=currentvalue

alist = [54,26,93,17,77,31,44,55,20]
shellSort(alist)
print(alist)
```

At first glance, one might think that a shell sort can't be better than an insertion sort, since it does a complete insertion sort as the last step. It turns out, however, that this final insertion sort doesn't need to do very many comparisons(or shifts) since the list has been pre-sorted by earlier incremental insertion sorts, as described above. In other words, each pass produces a list that is "more sorted" than the previous one. This makes the final pass very efficient.

Although a general analysis of the shell sort is well beyond the scope of this text, we can say that it tends to fall somewhere between ${O(n)}$ and ${O(n^{2})}$, based on the behavior described above. For the increments shown before, the performance in ${O(n^{2})}$. By changing the increment, for example using ${2^{k}-1}$(1, 3, 7, 15, 31, and so on), a shell sort can perform at ${O(n^{\frac{3}{2}})}$.

### The Merge Sort
We now turn our attention to using a divide and conquer strategy as a way to improve the performance of sorting algorithms. The first algorithm we'll study is the **merge sort**. Merge sort is a recursive algorithm that continually splits a list in half. If the list is empty or has one item, it is sorted by definition(the base case). If the list has more than one item, we split the list and recursively invoke a merge sort on both halves. Once the two halves are sorted, the fundamental operation, called a **merge**, is performed. merging is the process of taking two smaller sorted lists and combining them together into a single, sorted, new list. The figure below shows the familiar example list as it is being split by `mergeSort`. The figure below that shows the simple lists, now sorted, as they are merged back together.
![[Pasted image 20210624164132.png]]

![[Pasted image 20210624164150.png]]

The `mergeSort` function shown below begins by asking the base case question. If the length of the list is less than or equal to one, then we already have a sorted list and no more processing is necessary. If, on the other hand, the length is greater than one, then we use the Python `slice` operation to extract the left and right halves. It is important to note that the list may not have an even number of items. That doesn't matter, as the lengths will differ by at most one.
```python
def mergeSort(alist):
    print("Splitting ",alist)
    if len(alist)>1:
        mid = len(alist)//2
        lefthalf = alist[:mid]
        righthalf = alist[mid:]

        mergeSort(lefthalf)
        mergeSort(righthalf)

        i=0
        j=0
        k=0
        while i < len(lefthalf) and j < len(righthalf):
            if lefthalf[i] <= righthalf[j]:
                alist[k]=lefthalf[i]
                i=i+1
            else:
                alist[k]=righthalf[j]
                j=j+1
            k=k+1

        while i < len(lefthalf):
            alist[k]=lefthalf[i]
            i=i+1
            k=k+1

        while j < len(righthalf):
            alist[k]=righthalf[j]
            j=j+1
            k=k+1
    print("Merging ",alist)

alist = [54,26,93,17,77,31,44,55,20]
mergeSort(alist)
print(alist)
```

Once the `mergeSort` function is invoked on the left half and the right half(lines 8 - 9), it is assumed that they are sorted. The rest of the function(lines 11 - 31) is responsible for merging the two smaller sorted lists into a larger sorted list. Notice that the merge operation places the items back into the original list(`alist`) one at a time by repeatedly taking the smallest item from the sorted lists. Note that the statement `lefthalf[i] <= righthalf[j]` ensures that the algorithm is stable. A **stable algorithm** maintains the order of duplicate items in a list and is preferred in most cases.

The `mergeSort` function has been augmented with a `print` statement(line 2) to show the contents of the list being sorted at the start of each invocation. There is also a `print` statement(line 32) to show the merging process. The transcript shows the result of executing the function on the example list. Note that the list with 44, 55, and 20 will not divide evenly. The first split gives \[44\] and the second gives \[55, 20\]. It is easy to see how the splitting process eventually yields a list that can be immediately merged with other sorted lists.

In order to analyze the `mergeSort` function, we need to consider the two distinct processes that make up its implementation. First, the list is split into halves. We already computed(in a binary search) that we can divide a list in half ${log\hspace{0.2cm}n}$ times were *n* is the length of the list. The second process is the merge. Each item in the list will eventually be processed and placed on the sorted list. So the merge operation which results in a list of size *n* requires *n* operations. The result of this analysis is that ${log}$ *${n}$* splits, each of which costs *${n}$* for a total of *${n}$*  ${log}$ *${n}$* operations. A merge sort is an ${O(n\hspace{0.2cm}log\hspace{0.2cm}n)}$ algorithm.

Recall that the slicing operator is ${O(k)}$ where k is the size of the slice. In order to guarantee that `mergeSort` will be ${O(n\hspace{0.2cm}log\hspace{0.2cm}n)}$ we'll need to remove the slice operator. Again, this is possible if we simply pass the starting and ending indices along with the list when we make the recursive call.(left as exercise)

It is important to notice that the `mergeSort` function requires extra space to hold the two halves as they are extracted with the slicing operations. This additional space can be a critical factor if the list is large and can make this sort problematic when working on large data sets.

### The Quick Sort
 The **quick sort** uses divide and conquer to gain the same advantages as the merge sort, while not using additional storage. As a trade-off, however, it's possible that the list may not be divided in half. When this happens, the performance is diminished.
 
 A quick sort first selects a value, which is called the **pivot value**. Although there are many different ways to choose the pivot value, we will simply use the first item in the list. The role of the pivot value is to assist with splitting the list. The actual position where the pivot value belongs in the final sorted list, commonly called the **split point**, will be used to divide the list for subsequent calls to the quick sort.
 
 The figure below shows that 54 will serve as the first pivot value. Since we've looked at the example a few times already, we know that 54 will eventually end up in the position currently holding 31. The **partition** process will happen next. It will find the split point and at the same time move other items to the appropriate side of the list, either less than or greater than the pivot value.
 ![[Pasted image 20210626211305.png]]
 
 Partitioning begins by locating two position markers-- call them `leftmark` and `rightmark`-- at the beginning and end of the remaining items in the list(positions 1 and 8 in the figure below). The goal of the partition process is to move items that are on the wrong side with respect to the pivot value while also converging on the split point. The figure below shows this process as we locate the position of 54.
 ![[Pasted image 20210626211652.png]]
 
 We begin by incrementing `leftmark` until we locate a value that is greater than the pivot value. We then decrement `rightmark` until we find a value that is less than the pivot value. At this point we have discovered two items that are out of place with respect to the eventual split point. For the example, this occurs at 93 and 20. Now we can exchange these two items and then repeat the process again.
 
 At the point where `rightmark` becomes less than `leftmark`, we stop. The position of `rightmark` is now the split point. The pivot value can be exchanged with the contents of the split point and the pivot value is now in place(see below). In addition, all the items to the left of the split point are less than the pivot value, and all the items to the right of the split point are greater than the pivot value. The list can now be divided at the split point and the quick sort can be invoked recursively on the two halves.
 ![[Pasted image 20210626213157.png]]
 
 The `quickSort` function shown below invokes a recursive function, `quickSortHelper`. `quickSortHelper` begins with the same base case as the merge sort. If the length of the list is less than or equal to one, it is already sorted. If it is greater, then it can be partitioned and recursively sorted. The `partition` function implements the process described earlier.
 ```python
 def quickSort(alist):
   quickSortHelper(alist,0,len(alist)-1)

def quickSortHelper(alist,first,last):
   if first<last:

       splitpoint = partition(alist,first,last)

       quickSortHelper(alist,first,splitpoint-1)
       quickSortHelper(alist,splitpoint+1,last)


def partition(alist,first,last):
   pivotvalue = alist[first]

   leftmark = first+1
   rightmark = last

   done = False
   while not done:

       while leftmark <= rightmark and alist[leftmark] <= pivotvalue:
           leftmark = leftmark + 1

       while alist[rightmark] >= pivotvalue and rightmark >= leftmark:
           rightmark = rightmark -1

       if rightmark < leftmark:
           done = True
       else:
           temp = alist[leftmark]
           alist[leftmark] = alist[rightmark]
           alist[rightmark] = temp

   temp = alist[first]
   alist[first] = alist[rightmark]
   alist[rightmark] = temp


   return rightmark

alist = [54,26,93,17,77,31,44,55,20]
quickSort(alist)
print(alist)
```

To analyze the `quickSort` function, note that for a list of length *n*, if the partition always occurs in the middle of the list, there will again be ${log\hspace{0.2cm}n}$ divisions. In order to find the split poitn, each of the *n* items needs to be checked against the pivot value. The result is *${n}$* ${log}$ *${n}$*. In addition, there is no need for additional memory as in the merge sort process.

Unfortunately, in the worst case, the split points may not be in the middle and can be very skewed to the left or the right, leaving a very uneven division. In this case, sorting a list of *n* items divides into sorting a list of 0 items and a list of ${n-1}$ items. Then sorting a list of ${n-1}$ divides into a list of size 0 and a list of size ${n-2}$, and so on. The result is an  ${O(n^{2})}$ sort with all of the overhead that recursion requires.

It was mentioned earlier that there are different ways to choose the pivot value. In particular, we can attempt to alleviate some of the potential for an uneven division by using a technique called **median of three**. To choose the pivot value, we will consider the first, the middle, and the last element in the list. In the example, those are 54, 77, and 20. Now pick the median value, in our case 54, and use it for the pivot value(of course, that was the pivot value used originally). The idea is that in the case where the first item in the list doesn't belong toward the middle of the list, the median of the three will choose a better "middle" value. This will be particularly useful when the original list is somewhat sorted to begin with. The rest of the implementation in resources.