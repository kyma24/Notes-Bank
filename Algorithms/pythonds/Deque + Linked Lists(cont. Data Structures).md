A **deque**, or a double-ended queue, is an ordered collection of items similar to a queue. It has 2 ends, a front and a rear, and the items remain positioned in the collection. What makes a deque different is the unrestrictive nation of adding and removing items. New items can be added at either the front or the rear. Likewise, existing items can be removed from either end. In a sense, this hybrid linear structure provides all the capabilities of stacks and queues in a single data structure. Below shows a deque of Python data objects.

It is important to note that even though the deque can assume many of the characteristics of stacks and queues, it doesn't require the LIFO and FIFO orderings that are enforced by those data structures. It is up to you to make consistent use of the addition and removal operations.
![../_images/basicdeque.png](https://runestone.academy/runestone/books/published/pythonds/_images/basicdeque.png)

Deque operations:
- `Deque()` creates a new deque that is empty. It needs no parameters and returns an empty deque
- `addFront(item)` addes a new item to the front of the deque. It needs the item and returns nothing
- `addRear(item)` adds a new item to the rear of the deque. It needs the item and returns nothing.
- `removeFront()` removes the front item from the deque. It needs no parameters and returns the item. The deque is modified.
- `removeRear()` removes the rear item from the deque. It needs no parameters and returns the item. the deque is modified.
- `isEmpty()` tests to see whether the deque is empty. It needs no parameters and returns a boolean value.
- `size()` returns the number of items in the deque. It needs no parameters and returns an integer.

Implementing a deque:
```python
class Deque:
	def __init__(self):
		self.items = []
	
	def isEmpty(self):
		return self.items == []
		
	def addFront(self, item):
		self.items.append(item)
		
	def addRear(self, item):
		self.items.insert(0,item)
		
	def removeFront(self):
		return self.items.pop()
	
	def removeRear(self):
		return self.items.pop(0)
		
	def size(self):
		return len(self.items)
```

![[Pasted image 20210501082321.png]]

### Palindrome-Checker
![../_images/palindromesetup.png](https://runestone.academy/runestone/books/published/pythonds/_images/palindromesetup.png)

```python
from pythonds.basic import Deque

def palchecker(aString):
    chardeque = Deque()

    for ch in aString:
        chardeque.addRear(ch)

    stillEqual = True

    while chardeque.size() > 1 and stillEqual:
        first = chardeque.removeFront()
        last = chardeque.removeRear()
        if first != last:
            stillEqual = False

    return stillEqual

print(palchecker("lsdkjfskf"))
print(palchecker("radar"))
```

### The Unordered List Abstract Data Type
- `List()` creates  anew list that's empty. It needs no parameters and returns an empty list
- `add(item)` adds a new item to the list. It needs the item and returns nothing. Assume the item isn't already in the list
- `remove(item)` removes the item from the list. It needs the item and modifies the list. Assume the item is present in the list
- `search(item)` searches for the item in the list. It needs the item and returns a boolean value
- `isEmpty()` tests to see whether the list is empty. It needs no parameters and returns a boolean value
- `size()` returns the number of items in the list. It needs no parameters and returns an integer
- `append(item)` adds a new item to the end of the list making it the last item in the collection. It needs the item and returns nothing. Assume the item isn't already in the list
- `index(item)` returns the position of the item in the list. It needs the item and returns the idenx. Assume the item is in the list
- `insert(pos,item)` adds a new item to the list as position pos. It needs the item and returns nothing. Assume the item is not already in the list and there are enough existing items to have position pos
- `pop()` removes and returns the last item in the list. It needs nothing and returns an item. Assume the list has at least one item
- `pop(pos)` removes and returns the item at position pos. It needs the position and returns the item. Assume the item is in the list

### Linked Lists & implementing an Unordered List
In order to implement an unordered list, we will construct a **linked list**. Recall that we need to be sure that we can maintain the relative positioning of the items. However, there is no requirement that we maintain that positioning in contiguous memory. For example, consider the collection of items below. It appears that these values have been placed randomly. If we can maintain some explicit information about each item, namely the location of the next item, then the relative position of each item can be expressed by simply following the link from one item to the next.
![../_images/idea.png](https://runestone.academy/runestone/books/published/pythonds/_images/idea.png)
![../_images/idea2.png](https://runestone.academy/runestone/books/published/pythonds/_images/idea2.png)

It's important to note that the location of the first item of the list must be explicitly specified. Once we know where the first item is, the first item can tell us where the second is, and so on. The external reference is often referred to as the **head** of the list. Similarly, the last item needs to know that there is no next item.

### The `Node` Class
The basic building block for the linked list implementation is the **node**. Each node object must hold at least two pieces of information. First, the node must contain the list item itself. We will call this the **data field** of the node. In addition, each node must hold a reference to the next node. To constructo a node, you need to supply the initial data value for the node. Evaluating the assignment statement below will yield a node object containing the value 93. You should note that we will typically represent a node object as shown in the fourth picture. The `Node` class also includes the usual methods to access and modify the data and the next reference.
```python
class Node:
	def __init__(self,initdata):
		self.data = initdata
		self.next = None
		
	def getData(self):
		return self.data
	
	def getNext(self):
		return self.next
		
	def setData(self,newdata):
		self.data = newdata
		
	def setNext(self,newnext):
		self.next = newnext
```

Creating node objects:
```python
>>> temp = Node(93)
>>> temp.getData()
93
```

The special Python reference value `None` will play an important role in the `Node` class and later in the linked list itself. A reference to `None` will denote the fact that there is no next node. Note in the constructor that a node is initially created with `next` set to `None`. Since this is sometimes referred to as "grounding the node," we will use the standard ground symbol to denote a reference that is referring to `None`. It's always a good idea to explicitly assign `None` to the initial next reference values.

![../_images/node.png](https://runestone.academy/runestone/books/published/pythonds/_images/node.png)

![../_images/node2.png](https://runestone.academy/runestone/books/published/pythonds/_images/node2.png)

### The `Unordered List` Class
As suggested abv, the unordered list will be built from a collection of nodes, each linked to the next by explicit references. As long as we know where to find the first node(containing the item), each item after that can be found by successively following the next links. With this in mind, the `UnorderedList` class must maintain a reference to the first node. Below shows the constructor. Note that each list object will maintain a single reference to the head of the list.
```python
class UnorderedList:
	def __init__(self):
		self.head = None
```

Initially when we construct a list, there are no items. The assignment statement
```python
>>> mylist = UnorderedList()
```

creates the linked list representation shown below. As discussed in the `Node` class, the special reference `None` will again be used to state that the head of the list doesn't refer to anything. Eventually, the example list given earlier will be represented by a linked list as shown in the second image below. The head of the list refers to the first node which contains the first item of the list. In turn, that node holds a reference to the next node and so on. It's very important to note that the list class itself doesn't contain any node objects. Instead it contains a single reference to only the first node in the linked structure.
![../_images/initlinkedlist.png](https://runestone.academy/runestone/books/published/pythonds/_images/initlinkedlist.png)

![../_images/linkedlist.png](https://runestone.academy/runestone/books/published/pythonds/_images/linkedlist.png)

The `isEmpty` method is shown below.
```python
def isEmpty(self):
	return self.head == None
```

Now, we need to implement the `add` method. However, before we can do that, we need to address the important question of where in the linked list to place the new item. Since this list is unordered, the specific location of the new item with respect to the other items already in the list isn't important. The new item can go anywhere. With that in mind, it makes sense to place the new item in the easiest location possible.

Recall that the linked list structure provides us with only one entry point, the head of the list. All of the other nodes can only be reached by accessing the first node and then following `next` links. This means that the easiest place to add the new node is right at the head, or beginning of the list. In other words, we will make the new item the first item of the list and the existing items will need to be linked to this new first item so that they follow.

The linked list shown in the above picture was built by calling the `add` method a number of times.
```python
>>> mylist.add(31)
>>> mylist.add(77)
>>> mylist.add(17)
>>> mylist.add(93)
>>> mylist.add(26)
>>> mylist.add(54)
```

Note that since 31 is the first item added to the list, it will eventually be the last node on the linked list as every other item is added ahead of it. Also, since 54 is the last item added, it will become the data value in the first node of the linked list.

The `add` method is shown below. Each item of the list must reside in a node object. Line 2 creates a new node and places the item as its data. Now we must complete the process by linking the new node into the existing structure. This requires two steps as shown in the below picture. Step 1(line 3) change the `next` reference of the new node to refer to the old first node of the list. Now that the rest of the list has been properly attached to the new node, we can modify the head of the list to refer to the new node. The assignment statementin line 4 sets the head of the list.

The order of the two steps described abv is very important. What happens if the order of line 3 and line 4 is reversed? If the modification of the head of the list happens first, the result can be seen in the second image below. Since the head was the only external reference to the list nodes, all of the original nodes are lost and can no longer be accessed.
```python
def add(self,item):
	temp = Node(item)
	temp.setNext(self.head)
	self.head = temp
```

![../_images/addtohead.png](https://runestone.academy/runestone/books/published/pythonds/_images/addtohead.png)

![../_images/wrongorder.png](https://runestone.academy/runestone/books/published/pythonds/_images/wrongorder.png)

The next methods that will be implemented - `size`, `search`, and `remove` - are all based on a technique known as **linked list traversal**. Traversal refers to the process of systematically visiting each node. To do this we use an external reference that starts at the first node in the list. As we visit each node, we move the reference to the next node by "traversing" the next reference.

To implement the `size` method, we need to traverse the linked list and keep a count of the number of nodes that occured. Below is the Python code for counting the number of nodes in the list. The external reference is called `current` and is initialized to the head of the list in line 2. At the start of the process we haven't seen any nodes so the count is set to 0. Lines 4-6 actually implement the traversal. As long as the current reference hasn't seen the end of the list(`None`), we move current along to the next node via the assignment statement in line 6. Again, the ability to compare a reference to `None` is very useful. Every time current moves to a new node, we add 1 to the `count`. Finally, `count` gets returned after the iteration stops. The picture below shows this process as it proceeds down the list.
```python
def size(self):
	current = self.head
	count = 0
	while current != None:
		count = count + 1
		current = current.getNext()
	
	return count
```

![../_images/traversal.png](https://runestone.academy/runestone/books/published/pythonds/_images/traversal.png)

Searching for a value in a linked list implementation of an unordered list also uses the traversal technique. As we visit each node in the linked list we will ask whether the data stored there matches the item we are looking for. In this case, however, we may not have to traverse all the way to the end of the list. In fact, if we do get to the end of the list, that means that the item we are looking for must not be present. Also, if we do find the item, there is no need to continue.

Below shows the implementation for the `search` method. As in the `size` method, the traversal is initialized to start at the head of the list(line 2). We also use a boolean variable called `found` to remember whether we have located the item we are searching for. Since we haven't found the item at the start of the traversal, `found` can be set to `False`(line 3). The iteration in line 4 takes into account both conditions discussed above. As long as there are more nodes to visit and we haven't found the item we are looking for, we continue to check the next node. The question in line 5 asks whether the data item is present in the current node. If so, `found` can be set to `True`.
```python
def search(self,item):
	current = self.head
	found = False
	while current != None and not found:
		if current.getData() == item:
			found = True
		else:
			current = current.getNext()
	
	return found
```

As an example, consider invoking the `search` method looking for the item 17.
```python
>>> mylist.search(17)
True
```

Since 17 is in the list, the traversal process needs to move only to the node containing 17. At that point, the variable `found` is set to `True` and the `while` condition will fail, leading to the return value seen above. This process can be seen in the figure below.
![../_images/search.png](https://runestone.academy/runestone/books/published/pythonds/_images/search.png)

The remove method requires 2 logical steps. First, we need to traverse the list looking for the item we want to remove. Once we find the item(recall that we assume it's present), we must remove it. The first step is very similar to `search`. Starting with an external reference set to the head of the list, we traverse the links until we discover the item we are looking for. Since we assume that the item is present, we know that the iteration will stop before `current` gets to `None`. This means that we can simply use the boolean `found` in the condition.

When `found` becomes `True`, `current` will be a reference to the node containing the item to be removed. One possibility to do this would be to replace the value of the item with some marker that suggests that the item is no longer present. The problem with this approach is the number of nodes will no longer match the number of items. It would be much better to remove the item by removing the entire node.

In order to remove the node containing the item, we need to modify the link in the previous node so that it refers to the node that comes after `current`. Unfortunately, there is no way to go backward in the linked list. Since `current` refers to the node ahead of the node where we would like to make the change, it is too late to make the necessary modification.

The solution to this dilemma is to use two external references as we traverse down the linked list. `current` will behave just as it did before, marking the current location of the traverse. The new reference, which will be called `previous`, will always travel one node behind `current`. That way, when `current` stops at the node to be removed, `previous` will be referring to the proper place in the linked list for the modification.

The below code shows the complete `remove` method. Lines 2-3 assign initial values to the two references. Note that `current` starts out at the list head as in the other traversal examples. `previous`, however, is assumed to always travel one node behind current. For this reason, `previous` starts out with a value of `None` since there is no node before the head. The boolean variable `found` will again be used to control the iteration.

In lines 6-7 we ask whether the item stored in the current node is the item we wish to remove. If so, `found` can be set to `True`. If we don't find the item, `previous` and `current` must both be moved one node ahead. Again, the order of these two statements is crucial. `previous` must first be moved one node ahead to the location of `current`. At that point, `current` can be moved. This process is often referred to as "inch-worming" as `previous` must catch up to `current` before `current` moves ahead. The second picture below shows the movement of `previous` and `current` as they progress down the list looking for the node containing the value `17`.
```python
def remove(self,item):
	current = self.head
	previous = None
	found = False
	while not found:
		if current.getData() == item:
			found = True
		else:
			previous = current
			current = current.getNext()
	
	if previous == None:
		self.head = current.getNext()
	else:
		previous.setNext(current.getNext())
```

![../_images/removeinit.png](https://runestone.academy/runestone/books/published/pythonds/_images/removeinit.png)

![../_images/prevcurr.png](https://runestone.academy/runestone/books/published/pythonds/_images/prevcurr.png)

Once the searching step of the `remove` has been completed, we need to remove the node from the linked list. Below shows the link that must be modified. However, there is a special case that needs to be addressed. If the item to be removed happens to be the first item in the list, then `current` will reference the first node in the linked list. This also means that `previous` will be `None`. `previous` would be referring to the node whose next reference needs to be modified in order to complete the remove, so, in this case, it isn't `previous` but rather the head of the list that needs to be changed.

![../_images/remove.png](https://runestone.academy/runestone/books/published/pythonds/_images/remove.png)

![../_images/remove2.png](https://runestone.academy/runestone/books/published/pythonds/_images/remove2.png)

Line 12 allows us to check whether we are dealing with the special case described above. If `previous` didn't move, it will still have the value `None` when the boolean `found` becomes `True`. In that case(line 13) the head of the list is modified to refer to the node after the current node, which then removes the first node from the linked list. However, if previous != `None`, the node to be removed is elsewhere in the linked list structure. In this case the previous reference is providing us with the node whose next reference must be changed. Line 15 uses the `setNext` method from `previous` to accomplish the removal. Note that in both cases the destination of the reference change is `current.getNext()`.
```python
class Node:
    def __init__(self,initdata):
        self.data = initdata
        self.next = None

    def getData(self):
        return self.data

    def getNext(self):
        return self.next

    def setData(self,newdata):
        self.data = newdata

    def setNext(self,newnext):
        self.next = newnext


class UnorderedList:

    def __init__(self):
        self.head = None

    def isEmpty(self):
        return self.head == None

    def add(self,item):
        temp = Node(item)
        temp.setNext(self.head)
        self.head = temp

    def size(self):
        current = self.head
        count = 0
        while current != None:
            count = count + 1
            current = current.getNext()

        return count

    def search(self,item):
        current = self.head
        found = False
        while current != None and not found:
            if current.getData() == item:
                found = True
            else:
                current = current.getNext()

        return found

    def remove(self,item):
        current = self.head
        previous = None
        found = False
        while not found:
            if current.getData() == item:
                found = True
            else:
                previous = current
                current = current.getNext()

        if previous == None:
            self.head = current.getNext()
        else:
            previous.setNext(current.getNext())
        
    def append(self,item):
        current = self.head
        temp = Node(item)
        while current != None:
            current = current.getNext()
    
        current.setNext(temp)

    def insert(self, pos, item):
        current = self.head
        previous = None
        index = 0
        temp = Node(item)
        
        while current != None and index < pos:
            previous = current
            current = current.getNext()
            index += 1
        
        if pos == 0:
            temp.setNext(self.head)
            self.head = temp      
        else:
            if current == None:
                previous.setNext(temp)
            else:
                temp.setNext(current)
                previous.setNext(temp)

    def index(self, item):
        current = self.head
        found = False
        index = 0
        
        while current != None and not found:
            if current.getData() != item:
                index +=1
                current = current.getNext()
            else:
                found = True
            
        if found:
            return index
        else:
            return "Not Found"

    def pop(self):
        current = self.head
        previous = None
        
        if current == None:
            return "No item in list"
        
        while current.getNext() != None:
            previous = current
            current = current.getNext()
        
        previous.setNext(None)
        return current.getData()

    def delete(self, pos):
        current = self.head
        previous = None
        index = 0
        
        if current == None:
            return "No item in list"
        
        while index < pos and current != None:
            previous = current
            current = current.getNext()
            index += 1
          
        if current == None:
            return "No item in list"
        else:
            if previous == None:
                self.head = current.getNext()
            else:
                previous.setNext(current.getNext())
            return current.getData()

    
mylist = UnorderedList()

mylist.add(31)
mylist.add(77)
mylist.add(17)
mylist.add(93)
mylist.add(26)
mylist.add(54)

print(mylist.size())
print(mylist.search(93))
print(mylist.search(100))

mylist.add(100)
print(mylist.search(100))
print(mylist.size())

mylist.remove(54)
print(mylist.size())
mylist.remove(93)
print(mylist.size())
mylist.remove(31)
print(mylist.size())
print(mylist.search(93))
```