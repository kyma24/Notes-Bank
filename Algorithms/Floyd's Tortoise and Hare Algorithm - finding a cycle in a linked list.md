Idea behind algorithm: if have 2 pointers in linked list, one moving 2x as fast(the hare) than the other(the tortoise), then if they intersect, there is a cycle in the linked list. If they don't intersect, then there is no cycle.

In a problem, you are asked to return a boolean for whether or not there's a cycle. You're given the head of the linked list, and each node has a value(`.val`) and the next node can be found with `.next`.

First thing to do is to check if `head` exists, and if `head.next` exists. If neither do, then there's no cycle, and will immediately return false.

```python
def hasCycle(head):
	if head == None or head.next == None:
		return False
```

Next, will initiate a slow and fast pointer. The slow pointer(`tortoise`) will start at the head node. The fast pointer, `hare`, will start one step ahead, at head.next.
```python
def hasCycle(head):
	if head == None or head.next == None:
		return False
	tortoise = head
	hare = head.next
```

As long as the hare is still pointing at a node that isn't null, and the next node isn't null, will continue checking things. Therefore, a while loop would be most suitable.
```python
def hasCycle(head):
	if head == None or head.next == None:
		return False
	tortoise = head
	hare = head.next
	
	while hare != None and hare.next != None:
		#...
```

Inside the while loop, the first thing to do is to check if the tortoise & hare are pointing to the same node. If they are, that means it's a cycle, so we can return `true`.
```python
def hasCycle(head):
	if head == None or head.next == None:
		return False
		
	tortoise = head
	hare = head.next
	
	while hare != None and hare.next != None:
		if tortoise === hare:
			return True
		#...
```

Otherwise, we'll move the tortoise and hare. The tortoise moves one node at a time, and the hare moves two nodes at a time.
```python
def hasCycle(head):
	if head == None or head.next == None:
		return False
	tortoise = head
	hare = head.next
	
	while hare != None and hare.next !- None:
		if tortoise === hare:
			return True
		tortoise = tortoise.next
		hare = hare.next.next
		#...
```

Finally, if the while loop can't continue because `hare` and/or `hare.next` is null, then that means no cycle was ever found, so we can return `False`.
```python
def hasCycle(head):
	if head == None or head.next == None:
		return False
	
	tortoise = head
	hare = head.next
	
	while hare != None and hare.next != None:
		if tortoise === hare:
			return True
		tortoise = tortoise.next
		hare = hare.next
		
	return False
```

### How the Algorithm Works
Start with the linked list. The tortoise begins at the head, while the hare begins at head.next.
![Linked list with a cycle. Linked list is [1, 3, 2, 5], and after 5 the arrow points back to 3. Clipart of a tortoise on the first node, 1, and a hare on the second node, 3.](https://res.cloudinary.com/practicaldev/image/fetch/s--e_6wOF00--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/chpcvc0wjmpx2mi3l5l9.png)

Since hare and hare.next are both not null, we'll enter the while loop. tortoise and hare aren't equal to each other, so we'll move them both over. Tortoise gets moved over one spot, and hare moved over two spots.
![The tortoise and hare have moved. Hare is at the second node, 3, and tortoise is at the fourth node, 5.](https://res.cloudinary.com/practicaldev/image/fetch/s--KIRPAQyD--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/pwel97dag1dw06w37krn.png)

The while loop is stilll true. Again, the tortoise and hare aren't equal to each other. We'll move the tortoise over one, and the hare over two nodes.
![The tortoise and hare have moved. Hare is at the third node, 2, and tortoise as at the same node.](https://res.cloudinary.com/practicaldev/image/fetch/s--EIZkh61s--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/fe5sgzzti21d5nf6vumt.png)

The while loop is still true, but this time, tortoise and hare are equal to each other. This means that a cycle was found, so we will return True.




The question: finding duplicate number
The key here is to remember what the constraints were. The constraints are so specific because the problem wouldn't work if it wasn't: you wouldn't have to use Floyd's algorithm.

**Constraints**:
- Length of Array: n + 1
- Numbers are from 1 to n
(from pidgeonhole property, you know that one of the numbers have to be duplicated)
- Only ONE duplicate, but can be repeated multiple times 
^ to prevent using the ${\frac{n(n+1)}{2}}$ trick to solve the problem
- Time Complexity < ${O(n^{2})}$
^ could do < ${O(n\log n)}$, but they don't want you to know that it's definite linear time and give you some leeway.
- Array must not be modified
^ this is to prevent the user from taking advantage of the Time Complexity restraint and sorting the array to solve the problem
- Space has to be ${O(1)}$
^ to prevent the user from creating a copy of the array and sorting that one instead of the original, thus can't sort at all 

Moving on:

**Methods**:
1. Sort/Scan
	Time: ${O(n\log n)}$
	Space: ${O(1)}$
	Issue: Array Modified
2. Hash Map (Set)
	Time: ${O(n)}$
	Space: ${O(n)}$
	Issue: not space ${O(1)}$
	
Last one is Floyd's Algoithm.
You have two pointers, where one of them iterates the array going one by one and the other goes two by two, twice as far as the other.
![[Pasted image 20210718074135.png]]
![[Pasted image 20210718074234.png]]

Once they meet, you put one pointer back at the start and the other stays at the meeting point, this time both traversing one by one until they meet again at the place the cycle begins.
![[Pasted image 20210718074020.png]]
![[Pasted image 20210718074336.png]]

Here's why the pointers are guaranteed to hit the node at the start of the cycle:

Let's say **x** is the distance before the start of the cycle, and **y** is the distance from the start of the cycle, around to the meeting point. Lastly, we'll have **z**, which is the distance not yet covered. We'll say that **L** is y + z, or the length of the cycle.
![[Pasted image 20210718074818.png]]

To make things easier, we could add the definition of the meeting point as **M = x + y**.

Essentially, what we want to prove to prove that Floyd's Algorithm works is that ${x\mod{L} = z}$.
We can imagine a much larger ${x}$ with a ${L}$ cycle at the end. The ${x}$ could fit, for example, two ${L}$'s and a value ${a}$. Thus, ${x = L + L + a}$.  If we draw out ${z}$, what we want to prove is that ${a}$ is ${z}$.

We can do this by doing a bit of math.

**Turtle distance**: x + y

(There is a small proof that needs to be done, and that is why/how the turtle doesn't loop the cycle over and over again and reaches the meeting point in more than one cycle. It's pretty easy to prove that the turtle will never make a full cycle before the hare catches up to him.)

**Hare distance**: 2(x + y)

To make an equation to solve, first, we need to find some other way to represent the Hare's distance. Because the Hare could travel multiple times around the cycle before landing on the meeting point simultaenously with the turtle, the distance could be described by ${M + k * L}$ where **k** is a constant that represents how many cycles the hare traveled before meeting with the turtle. This could also be represented with ${x + y + k * L}$. This isn't the right order, of course; first, we traveled the x distance, and then the k x L, and finally the y distance before landing on the meeting point.
$$
2(x + y) = x + y + k * L
$$
$$
x + y = k * L
$$
$$
x = k * L - y
$$

Now, we're going to mod them on either side.
$$
x\mod L = (k*L - y)\mod L
$$
$$
x\mod L = (L + L + ...L - y)\mod L
$$
$$
x\mod L = L - y
$$

By getting rid of all the k L's and being left with L - y, which is z, we prove that the Floyd's Algorithm actually works.

Here is the way to use it for finding a duplicate number:
```python
# Python 3 program to find a duplicate
# element in an array with values in
# range from 0 to n-1.
 
# function to find one duplicate
def findduplicate(arr, n):
 
    # return -1 because in these cases
    # there can not be any repeated element
    if (n <= 1):
        return -1
 
    # initialize fast and slow
    slow = arr[0]
    fast = arr[arr[0]]
 
    # loop to enter in the cycle
    while (fast != slow) :
 
        # move one step for slow
        slow = arr[slow]
 
        # move two step for fast
        fast = arr[arr[fast]]
 
    # loop to find entry point of the cycle
    fast = 0
    while (slow != fast):
        slow = arr[slow]
        fast = arr[fast]
    return slow
 
# Driver Code
if __name__ == "__main__":
     
    arr = [1, 2, 3, 4, 5, 6, 3 ]
    n = len(arr)
    print(findduplicate(arr, n))
```