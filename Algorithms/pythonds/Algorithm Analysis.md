Algorithm - generic, step-by-step list of instructions for solving a problem; method for solving any instance of the problem such that given a particular input, the algorithm produces the desired result.

Program - algorithm that has been encoded into some programming language. May be many programs for the same algorithm, depending on programmer & programming language.

Consider function below. It solves a simple problem: computing the sum of the first *n* integers. The algorithm uses the idea of an accumulator variable that is initialized to 0. The solution then iterates through the *n* integers, adding each to the accumulator.
```python
def sumOfN(n):
	theSum = 0
	for i in range(1,n+1):
		theSum = theSum+i
		
	return theSum
	
print(sumOfN(10))
```

If make a program that does the same thing, except the names are all nonsensical(i.e. bill, tom, barney, foo, etc.), that would be poor coding(readability wise).
```python
def foo(tom):
	fred = 0
	for bill in range(1,tom+1):
		barney = bill
		fred = fred + barney
	
	return fred
	
print(foo(10))
```

However, algorithm analysis is concerned with comparing algorithms based upon the amount of computing resources that each algorithm uses. We want to be able to consider two algorithms and say that one is better than the other bc it is more efficient in its use of those resources or perhaps because it simply uses fewer. From this perspective, the two functions above seem very similar. They both use essentially the same algorithm to solve the summation problem.

At this point, it is important to think more abt what we really mean by computing resources. There are two different ways to look at this. One way is to consider the amount of space/memory an algorithm requires to solve the problem. The amount of space required by a problem solution is typically dictated by the problem instance itself. Every so often, however, there are algorithms that have very specific space requirements, and in those cases we will be very careful to explain the variations.

As an alternative to space requirements, we can analyze and compare algorithms based on the amount of time they require to execute(runtime). This can be measured by inserting these snippets of code in their respective areas:
```python
import time

def funcName(a):
	start = time.time()
	# code
	end = time.time()
	
	return randomVar, end-start
```

Now consider the code below, using the ${\frac{(n)(n+1)}{2}}$ algorithm, without iterating.
```python
def sumOfN3(n):
	return (n*(n+1))/2
	
print(sumOfN3(10))
```

From O(n) to O(1), and the time difference is very evident as the sums are executed in less than ${1}$ x ${10^{-4}}$ seconds.

###  Big-O Notation
A good basic unit of computation for comparing he summation algorithms earlier might be to count the number of assignment statements performed to compute the sum. In the function `sumOfN`, the number of assignment statements is 1 ${(theSum = 0)}$ plus the value of *n*(the number of times we perform ${theSum = theSum + i}$). We can denote this by a function, call it T, where ${T(n) = 1 + n}$. The parameter *n*  is often referred to as the "size of the problem", and we can read this as "T(n) is the time it takes to solve a problem of size n, namely 1+n steps."

In the summation functions abv, it makes sense to use the number of terms in the summation to denote the size of the problem. We can then say that the sum of the first 100,000 integers is a bigger instance of the summation problem than the sum of the first 1,000. Because of this, it might seem reasonable that the time required to solve the larger case would be greater than for the smaller case. The goal is to show how the algorithm's execution time changes with respect to the size of the problem.

Computer scientists prefer to take this analysis technique one step further. It turns out that the exact number of operations isn't as important as determining the most dominant part of the ${T(n)}$ function. In other words, as the problem gets larger, some portion of the ${T(n)}$ function tends to overpower the rest. This dominant term is what, in the end, is used for comparison. The **order of magnitude** function describes the part of ${T(n)}$ that increases the fastest as the value of *n* increases. Order of magnitude is often called **Big-O** notation(for "order") and written as ${O(f(n))}$. It  provides a useful approximation to the actual number of steps in the computation. The function ${f(n)}$ provides a simple representation of the dominant part of the original ${T(n)}$.

In the abv example, ${T(n) = 1 + n}$. As *n* gets large, the constant 1 will become less and less significant to the final result. If we are looking for an approximation for ${T(n)}$, then we can drop the 1 and simply say that the running time is ${O(n)}$. It is important to note that the 1 is certainly significant for ${T(n)}$. However, as *n* gets large, the approximation will be just as accurate without it.

As another example, suppose that for some algorithm, the exact number of steps is ${T(n) = 5n^{2} + 27n + 1005}$. When *n* is small, say 1 or 2, the constant 1005, seems to be the dominant part of the function. However, as *n* gets larger, the ${n^2}$ term becomes the most important. In fact, when *n* is really large, the other two terms become insignificant in the role that they play in determining the final result. Again, to approximate ${T(n)}$ as *n* gets large, we can ignore the other terms and focus on ${5n^{2}}$. In addition, the coefficient 5 becomes insignificant as *n* gets large. We would say then that the function ${T(n)}$ has an order of magnitude ${f(n) = n^{2}}$, or simply that it is ${O(n^{2})}$.

Although we don't see this in the summation example, sometimes the performance of an algorithm depends on the exact values of the data rather than simply the size of the problem. For these kinds of algorithms we need to characterize their performance in terms of **best case**, **worst case**, or **average case** performance. The worst case performance refers to a particular data set where the algorithm performs especially poorly. Whereas a different data set for the exact same algorithm might have extraordinarily good performance. However, in most cases the algorithm performs somewhere in between these two extremes(average case). It is important for a computer scientist to understand these distinctions so they aren't misled by one particular case.

A number of very common order of magnitude functions will come up over and over in the studying of algorithms. These are shown in the below table. In order to decide which of these functions is the dominant part of any ${T(n)}$ function, we must see how they compare with one another as *n* gets large.

f(n) | Name
---- | ----
1 | Constant
log n | Logarithmic
n | Linear
n log n | Log Linear
${n^2}$ | Quadratic
${n^3}$ | Cubic
${2^n}$ | Exponential

Below figure shows the common functions from the table above. Notice that when *n* is small, the functions aren't very well defined with respect to one another. It's hard to tell which is dominant. However, as *n* grows, there is a definite relationship and it's easy to see how they compare w/ one another.
![../_images/newplot.png](https://runestone.academy/runestone/books/published/pythonds/_images/newplot.png)

As a final example, suppose we have the fragment of Python code below. Although this program doesn't really do anything, it's instructive to see how we can take actual code and analyze performance.
```python
a = 5
b = 6
c = 10
for i in range(n):
	for j in range(n):
		x = i * i
		y = j * j
		z = i * j
for k in range(n):
	w = a*k + 45
	v = b*b
d = 33
```

The number of assignment operations is the sum of the four terms. The first term is the constant 3, representing the three assignment statements at the start of the fragment. The second term is ${3n^{2}}$, since there are three statements taht are performed ${n^{2}}$ times due to the nested iteration. The third item is ${2n}$, two statements iterated *n* times. Finally, the fourth term is the constant 1, representing the final assignment statement. This gives us ${T(n) = 3 + 3n^{2} + 2n + 1 = 3n^{2} + 2n + 4}$. By looking at the exponents, we can easily see that the ${n^{2}}$ term will be dominant and therefore this fragment of code is ${O(n^{2})}$. Note that all of the other terms as well as the coefficient on the dominant term can be ignored as *n* grows larger.
![../_images/newplot2.png](https://runestone.academy/runestone/books/published/pythonds/_images/newplot2.png)

### An Anagram Detection Example
A good example problem for showing algorithms with different orders of magnitude is the classic anagram detection problem for strings. One string is an anagram of another if the second is simply a rearrangement of the first. For example, `'heart'` and `'earth'` are anagrams. The strings `'python'` and `'typhon'` are anagrams as well. For the sake of simplicity, we will assume that the two strings in question are of equal length and that they are made up of symbols from the set of 26 lowercase alphabetic characters. The goal is to write a boolean function that will take two strings and return whether they are anagrams.

#### Solution 1: Checking Off
The first solution to the anagram problem will check the lengths of the strings and then to see that each character in the first string actually occurs in the second. If it is possible to "checkoff" each character, then the two strings must be anagrams. Checking off a character will be accomplished by replacing it with the special Python value `None`. However, since strings in Python are immutable, the firs step in the process will be to convert the second string into a list. Each character from the first string can be checked against the characters in the list and if found, checed off by replacement.
```python
def anagramSolution(s1,s2):
	stillOK = True
	if len(s1) != len(s2):
		stillOK = False
		
	alist = list(s2)
	pos1 = 0
	
	while pos1 < len(s1) and stillOK:
		pos2 = 0
		found = False
		while pos2 < len(alist) and not found:
			if s1[pos1] == alist[pos2]:
				found = True
			else:
				pos2 = pos2 + 1
		if found:
			alist[pos2] = None
		else:
			stillOK = False
			
		pos1 = pos1 + 1
	
	return stillOK
	
print(anagramSolution1('abcd', 'dcba'))
```

To analyze this algorithm, we need to note that each of the *n* characters in `s1` will cause an iteration through up to *n* characters in the list form `s2`. Each of the *n* positions in the list will be visited once to match a character from `s1`. The number of visits then becomes the sum of the integers from 1 to *n*. This can be written as
$$
\sum\limits_{i=1}^{n}i = \frac{n(n+1)}{2}
$$
$$
\hspace{1.2cm}=\frac{1}{2}n^{2} + \frac{1}{2}n
$$

As ${n}$ gets large, the ${n^{2}}$ term will dominate the ${n}$ term and the ${\frac{1}{2}}$ can be ignored. Therefore, this solution is ${O(n^{2})}$.

#### Solution 2: Sort and Compare
Another solution will make use of the fact that even though `s1` and `s2` are different, they are anagrams only if they consist of exactly the same characters. So if we begin by sorting each string alphabetically, from a to z, we will end up with the same string if the original two strings are anagrams. Below shows the solution. Again, in Python we can use the built-in `sort` method on lists by simply converting each string ot a list at the start.
```python
def anagramSolution2(s1, s2):
	alist1 = list(s1)
	alist2 = list(s2)
	
	alist1.sort()
	alist2.sort()
	
	pos = 0
	matches = True
	
	while pos < len(s1) and matches:
		if alist1[pos] == alist2[pos]:
			pos = pos + 1
		else:
			matches = False
	return matches
	
print(anagramSolution2('abcde', 'edcba'))
```

at first glance you amy be tempted to think that this algorithm is ${O(n)}$, since there is one simple iteration to compare the *n* characters after the sorting process. However, the two calls to the Python `sort` method aren't without their own cost. Sorting itself is typically either ${O(n^{2})}$ or ${O(n\hspace{0.2cm}log\hspace{0.2cm}n)}$, so the sorting operations dominate the iteration. In the end, this algorithm will have the same order of magnitude as that of the sorting process.

#### Solution 3: Brute Force
A **brute force** technique for solving a problem typically tries to exhaust all possibilities. For the anagram detection problem, we can simply generate a list of all possible strings using the characters from `s1` and then see if `s2` occurs. However, there is a difficulty with this approach. When generating all possible strings from `s1`, there are *n* possible first characters, ${n-1}$ possible characters for the second position, ${n-2}$ for the third, and so on, so the total number of candidate strings is ${n!}$.  Although some of the strings may be duplicates, the program can't know this ahead of time and so it will still generate ${n!}$ different strings.

it turns out that ${n!}$ grows even faster than ${2^{n}}$ as *n* gets large. In fact, if `s1` were 20 character long, there would be ${20! = 2,432,902,008,176,640,000}$ possible candidate strings. If we processed one possibility every second, it would still take us 77,146,816,596 years to go through the entire list. This is probably not going to be a good solution.

#### Solution 4: Count and Compare
One final solution to the anagram problem takes advantage of the fact that any two anagrams will have the same number of a's, the same number of b's, the same number of c's, and so on. In order to decide whether two strings are anagrams, we will first count the number of times each character occurs. Since there are 26 possible haracters, we can use a list of 26 counters, one for each possible character. Each time we see a particular character, we will increment the counter at that position. In the end, if the two lists of counters are identical, the strings must be anagrams.
```python
def anagramSolution4(s1,s2):
	c1 = [0]*26
	c2 = [0]*26
	
	for i in range(len(s1)):
		pos = ord(s1[i]) - ord('a')
		c1[pos] = c1[pos] + 1
	
	for i in range(len(s2)):
		pos = ord(s2[i]) - ord('a')
		c2[pos] = c2[pos] + 1
		
	j = 0
	stillOK = True
	while j < 26 and stillOK:
		if c1[j] == c2[j]:
			j = j + 1
		else:
			stillOK = False
	
	return stillOK
	
print(anagramSolution4('apple', 'pleap'))
```

Again, the solution has a number of iterations. However, unlike the first solution, none of them are nested. The first two iterations used to count the characters are both based on *n*. The third iteration comparing the two lists of counts, always takes 26 steps since there are 26 possible characters in the strings. Adding it all up gives us ${T(n) = 2n + 26}$ steps. That is ${O(n)}$. We have found a linear order of magnitude algorithm for solving this problem.

Although the last solution was able to run in linear time, it could only do so by using additional storage to keep the two lists of character counts. In other words, this algorithm sacrificed space in order to gain time.

This is a common occurrence. On many occasions you will need to make the decisions between time and space trade-offs. In this case, the amount of extra space isn't significant. However, if the underlying alphabet had millions of characters, there would be more concern. As a computer scientist, when given a choice of algorithms, it will be up to you to determine the best use of computing resources given a particular problem.

### Lists
There are 4 different ways we might generate a list of `n` numbers starting with 0.
```python
def test1():
	l = []
	for i in range(1000):
		l = l + [i]

def test2():
	l = []
	for i in range(1000):
		l.append(i)
		
def test3():
	l = [i for i in range(1000)]
	
def test4():
	l = list(range(1000))
```

To capture the time it takes for each of the functions to execute we will use Python's `timeit` module.
```python
t1 = Timer("test1()", "from __main__ import test1")
print("concat ", t1.timeit(number=1000), "milliseconds")
t2 = Timer("test2()", "from __main__ import test2")
print("append ", t2.timeit(number=1000), "milliseconds")
t3 = Timer("test3()", "from __main__ import test3")
print("comprehension ", t3.timeit(number=1000), "milliseconds")
t4 = Timer("test4()", "from __main__ import test4")
print("list range ", t4.timeit(number=1000), "millseconds")

concat  6.54352807999 milliseconds
append  0.306292057037 milliseconds
comprehension  0.147661924362 milliseconds
list range  0.0655000209808 milliseconds
```

In the experiment abv the statement that we are timing in the function call to `test1()`, `test2()`, and so on. The setup statement may look very strange, so here is the explanation. The statement `from __main__ import test1` imports the function `test1` from the `__main__` namespace into the namespace that `timeit` sets up for the timing experiment. The `timeit` module does this because it wants to run the timing tests in an environment that is uncluttered by any stray variables that may have been created, that may interfere with the function's performance in some unforseen way.

From the experiment above it is clear that the append operation at 0.30 milliseconds is much faster than concatenation at 6.54 milliseconds. In the above experiment we also show the times for two additional methods for creating a list; using the list constructor with a call to `range` and a list comprehension. It is interesting to note that the list comprehension is twice as fast as a `for` loop with an `append` operation.

One final observation about this little experiment is that all of the times that you see above include some overhead for actually calling the test function, but we can assume that the function call overhead is identical in all four cases so we still get a meaningful comparison of the operations. So it wouldn't be accurate to say that the concatenation takes 6.54 milliseconds but rather the concatenation test function takes 6.54 milliseconds.

Here are the Big-O efficiencies for some of the common operations:
Operation | Big-O Efficiency
---------------|--------------
index\[\] | O(1)
index assignment | O(1)
append | O(1)
pop() | O(1)
pop(i) | O(n)
insert(i, item) | O(n)
del operator | O(n)
iteration | O(n)
contains (in) | O(n)
get slice \[x:y\] | O(k)
del slice | O(n)
set slice | O(n+k)
reverse | O(n)
concatenate | O(k)
sort | O(n log n)
multiply | O(nk)

Here are the Big-O efficiencies of Python Dictionary Operations
Operation | Big-O Efficiency
---------------|-------------
copy | O(n)
get item | O(1)
set item | O(1)
delete item | O(1)
contains (in) | O(1)
iteration | O(n)