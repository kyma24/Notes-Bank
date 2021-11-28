- `OrderedList` creates a new ordered list that's empty. It needs no parameters and returns an empty list
- `add(item)` adds a new item to the list making sure that the order is preserved. It needs the item and returns nothing. Assume the item isn't already in the list.
- `remove(item)` removes the item from the list. It needs the item and modifies the list. Assume the item is present in the list.
- `search(item)` searches for the item in tthe list. It needs the item and returns a boolean value
- `isEmpty()` tests to see whether the list is empty. It needs no parameters and returns a boolean value
- `size()` returns the number of items in the list. It needs no parameters and returns an integer
- `index(item)` returns the position of the item in the list. It needs the item and returns the index. Assume the item is in the list.
- `pop()` removes and returns the last item in the list. It needs nothing and returns an item. Assume the list has at least one item.
- `pop(pos)` removes and returns the item at position pos. It needs the position and returns the item. Assume the item is in the list. 

### Implementing an Ordered List
In order to implement the ordered list, we must remember that the relative positions of the items are based on some underlying characteristic. The ordered list of integers 17, 26, 31, 54, 77, and 93 can be represented by a linked structure as shown below. Again, the node and link structure is ideal for representing the relative positioning of the items.
![../_images/orderlinkedlist.png](https://runestone.academy/runestone/books/published/pythonds/_images/orderlinkedlist.png)

To implement the `OrderedList` class, we will use the same technique as seen previously with unordered lists. Once again, an empty list will be denoted by a `head` reference to `None`.
```python
class OrderedList:
	def __init__(self):
		self.head = None
```

When considering operations for ordered list, should note that the `isEmpty` and `size` methods can be implemented the same as w/ unordered lists since they deal only w/ the number of nodes in the list w/o regard to the actual item values. Likewise, the `remove` method will work just fine since we still need to find the item & then link around the node to remove it. The two remaining methods, `search` and `add`, will require some modification.

The search of an unordered linked list required that we traverse the nodes one at a time until we either find the item we're looking for or run out of nodes(`None`). It turns out that the same approach will work w/ the ordered list & in the case where we find the item it is exactly what we need. However, in the case where the item isn't in the list, we can take advantage of the ordering to stop the search as soon as possible.

i.e. below shows the ordered linked list as a search is looking for the value 45. As we traverse, starting at the head of the list, we first compare against 17. Since 17 isn't the item we're looking for, we move to the next node, in this case 26. Again, this isn't what we want, so we move onto 31 and then onto 54. Now, at this point, something is different. Since 54 isn't the item we're looking for, the former strategy would be to move forward. However, due to the fact that this is an ordered list, that won't be necessary. Once the value in the node becomes greater than the item we're searching for, the search can stop & return `False`. There's no way the item could exist further out in the linked list.
![../_images/orderedsearch.png](https://runestone.academy/runestone/books/published/pythonds/_images/orderedsearch.png)

Below shows the complete `search` method. It's easy to incorporate the new condition discussed abv by adding another boolean variable, `stop`, and initializing it to `False`(line 4). While `stop` is `False`(not `stop`) we can continue to look forward in the list(line 5). If any node is ever discovered that contains data greater than the item we're looking for, will set `stop` to `True`(lines 9-10). The remaining lines are identical to the unordered list search.
```python
def search(self,item):
	current = self.head
	found = False
	stop = False
	while current != None and not found and not stop:
		if current.getData() == item:
			found = True
		else:
			if current.getData() > item:
				stop = True
			else:
				current = current.getNext()
				
	return found
```

The most significant method modification will take place in `add`. Recall that for unordered lists, the `add` method could simply place a new node at the head of the list. It was the easiest point of access. Unfortunately, this'll no longer work with ordered lists. It is now necessary that we discover the specific place where a new item belongs in the existing ordered list.

Assume that we have the ordered list consisting of 17, 26, 54, 77, and 93 and we want to add the value 31. The `add` method must decide that the new item belongs between 26 and 54. The figure below shows the setup that we need. As explained earlier, we need to traverse the linked list looking for the place where the new node will be added. We know that we have found that place when either we run out of nodes(`current` becomes `None`) or the value of the current node becomes greater than the item we wish to add. In the example, seeing the value 54 causes us to stop.
![../_images/linkedlistinsert.png](https://runestone.academy/runestone/books/published/pythonds/_images/linkedlistinsert.png)

As seen with unordered lists, it's necessary to have an additional reference, again called 	`previous`, since `current` won't provide access to the node that must be modified. The code below shows the complete `add` method. Lines 2-3 set up the two external references and lines 9-10 again allow `previous` to follow one node behind `current` every time through the iteration. The condition(line 5) allows the iteration to continue as long as there are more nodes and the value in the current node is not larger than the item. In either case, when the iteration fails, we have found the location for the new node.

The remainder of the method completes the two step process shown in the picture above. Once a new node has been created for the item, the only remaining question is whether the new node will be added at the beginning of the linked list or some place in the middle. Again, `previous == None`(line 13) can be used to provide the answer.
```python
def add(self,item):
	current = self.head
	previous = None
	stop = False
	while current != None and not stop:
		if current.getData() > item:
			stop = True
		else:
			previous = current
			current = current.getNext()
			
	temp = Node(item)
	if previous == None:
		temp.setNext(self.head)
		self.head = temp
	else:
		temp.setNext(current)
		previous.setNext(temp)
```

The `OrderedList` class with methods discussed thus far can be found below.
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


class OrderedList:
    def __init__(self):
        self.head = None

    def search(self,item):
        current = self.head
        found = False
        stop = False
        while current != None and not found and not stop:
            if current.getData() == item:
                found = True
            else:
                if current.getData() > item:
                    stop = True
                else:
                    current = current.getNext()

        return found

    def add(self,item):
        current = self.head
        previous = None
        stop = False
        while current != None and not stop:
            if current.getData() > item:
                stop = True
            else:
                previous = current
                current = current.getNext()

        temp = Node(item)
        if previous == None:
            temp.setNext(self.head)
            self.head = temp
        else:
            temp.setNext(current)
            previous.setNext(temp)

    def isEmpty(self):
        return self.head == None

    def size(self):
        current = self.head
        count = 0
        while current != None:
            count = count + 1
            current = current.getNext()

        return count


mylist = OrderedList()
mylist.add(31)
mylist.add(77)
mylist.add(17)
mylist.add(93)
mylist.add(26)
mylist.add(54)

print(mylist.size())
print(mylist.search(93))
print(mylist.search(100))
```

```python
# full version
class List:
    def __init__(self, head: Node = None, tail: Node = None):
        self.head = head
        self.tail = tail
    def __init__(self):
        self.head: Node = None
        self.tail: Node = None

    def isEmpty(self):
    def is_empty(self) -> bool:
        return self.head is None

    def numberOfElements(self)->int:
        if self.isEmpty():
            return 0
        else:
            current: Node = self.head
            stopped: bool = True
            count: int = 0
            while current != self.head or stopped:
                stopped = False
                count += 1
                current = current.next
            return count

    def printAll(self):
        if self.isEmpty():
    def print_all(self):
        if self.is_empty():
            return
        else:
            current: Node = self.head
            stopped: bool = True
            while current != self.head or stopped:
                stopped = False
                print(current.key, end=", ")
                current = current.next
            print("")

    def addToHead(self, key):
        if self.isEmpty():
        tmp: Node = self.head
        stopped: bool = False
        while not stopped:
            print(tmp.key, end=", ")
            tmp = tmp.next
            if tmp == self.head:
                stopped = True
        print("")

    def number_of_elements(self) -> int:
        if self.is_empty():
            return 0
        count: int = 0
        tmp: Node = self.head
        stopped: bool = False
        while not stopped:
            count += 1
            tmp = tmp.next
            if tmp == self.head:
                stopped = True
        return count

    def add_to_head(self, key: int):
        if self.is_empty():
            self.head = self.tail = Node(key)
            self.head.prev = self.tail
            self.tail.next = self.head
@@ -43,8 +44,8 @@ def addToHead(self, key):
            self.head.next.prev = self.head
            self.tail.next = self.head

    def addToTail(self, key):
        if self.isEmpty():
    def add_to_tail(self, key: int):
        if self.is_empty():
            self.head = self.tail = Node(key)
            self.head.prev = self.tail
            self.tail.next = self.head
@@ -53,132 +54,115 @@ def addToTail(self, key):
            self.tail = self.tail.next
            self.head.prev = self.tail

    def deleteFromHead(self):
        if self.isEmpty():
    def delete_from_head(self) -> int:
        if self.is_empty():
            return None
        else:
            retValue = self.head.key
            ret_node: Node = self.head
            if self.head == self.tail:
                self.head = self.tail = None
            else:
                self.head = self.head.next
                self.head.prev = self.tail
                self.tail.next = self.head
            return retValue
            return ret_node.key

    def deleteFromTail(self):
        if self.isEmpty():
    def delete_from_tail(self) -> int:
        if self.is_empty():
            return None
        else:
            retValue = self.tail.key
            ret_node: Node = self.tail
            if self.head == self.tail:
                self.head = self.tail = None
            else:
                self.tail = self.tail.prev
                self.head.prev = self.tail
                self.tail.next = self.head
            return retValue

    def deleteNodesWithValue(self, value):
        if self.isEmpty():
            return
        else:
            current: Node = self.head
            stopped: bool = True
            while current.next != self.head or stopped:
                stopped = False
                if current.next.key == value:
                    current.next = current.next.next
                    current.next.prev = current
                else:
                    current = current.next
            self.tail = current
            self.tail.next = self.head
            self.head.prev = self.tail
            if self.head.key == value:
                self.deleteFromHead()
                self.head.prev = self.tail
            return ret_node.key

    def deleteOnIndex(self, index: int):
        if self.isEmpty():
            return 
        else:
            lastIndex = self.numberOfElements() - 1
            if index < 0 or index > lastIndex:
                print("Index out of range")
                return
    def delete_nodes_with_value(self, key: int):
        if self.is_empty():
            return None
        ret_value: int = None
        tmp: Node = self.head
        while tmp.next != self.head:
            if tmp.next.key == key:
                ret_value = tmp.next.key
                tmp.next = tmp.next.next
                tmp.next.prev = tmp
            else:
                if index == 0:
                    self.deleteFromHead()
                elif index == lastIndex:
                    self.deleteFromTail()
                else:
                    current: Node = self.head
                    count: int = 0
                    while count < index:
                        current = current.next
                        count += 1
                    current.prev.next = current.next
                    current.next.prev = current.prev

    def insertAfter(self, listElement: int, newElement: int):
        if self.isEmpty():
                tmp = tmp.next
        self.tail = tmp
        if self.head.key == key:
            ret_value = self.delete_from_head()
        return ret_value

    def delete_on_index(self, index: int):
        if self.is_empty():
            return
        else:
            current: Node = self.head
            stopped: bool = True
            while current != self.head or stopped:
                stopped = False
                if current.key == listElement:
                    if current == self.tail:
                        self.addToTail(newElement)
                    else:
                        newNode = Node(newElement, current, current.next)
                        newNode.prev.next = newNode
                        newNode.next.prev = newNode
                    current = current.next
                current = current.next

    def insertBefore(self, listElement, newElement):
        if self.isEmpty():
        end_index: int = self.number_of_elements() - 1
        if index < 0 or index > end_index:
            return
        if index == 0:
            self.delete_from_head()
        elif index == end_index:
            self.delete_from_tail()
        else:
            current: Node = self.head
            stopped: bool = True
            while current != self.head or stopped:
                stopped = False
                if current.key == listElement:
                    if current == self.head:
                        self.addToHead(newElement)
                    else:
                        newNode = Node(newElement, current.prev, current)
                        newNode.prev.next = newNode
                        newNode.next.prev = newNode
                current = current.next
            tmp: Node = self.head
            count: int = 0
            while count < index:
                tmp = tmp.next
                count += 1
            tmp.prev.next = tmp.next
            tmp.next.prev = tmp.prev

    def sort(self):
        if self.isEmpty():
    def insert_after(self, list_element: int, new_element: int):
        if self.is_empty():
            return
        else:
            outer: Node
            inner: Node
            while outer != self.tail:
                inner = self.tail
                while inner != outer:
                    if inner.prev.key > inner.key:
                        tmp: int = inner.key
                        inner.key = inner.prev.key
                        inner.prev.key = tmp
                    inner = inner.prev
                outer = outer.next







        tmp: Node = self.head
        stopped: bool = False
        while not stopped:
            if tmp.key == list_element:
                if tmp == self.tail:
                    self.add_to_tail(new_element)
                else:
                    new_node = Node(new_element, tmp, tmp.next)
                    tmp.next = new_node
                    new_node.next.prev = new_node
                tmp = tmp.next
            tmp = tmp.next
            if tmp == self.head:
                stopped = True

    def insert_before(self, list_element: int, new_element: int):
        if self.is_empty():
            return
        tmp: Node = self.head
        stopped: bool = False
        while not stopped:
            if tmp.key == list_element:
                if tmp == self.head:
                    self.add_to_head(new_element)
                else:
                    new_node = Node(new_element, tmp.prev, tmp)
                    new_node.prev.next = new_node
                    tmp.prev = new_node
            tmp = tmp.next
            if tmp == self.head:
                stopped = True


    def sort(self):
        swapped: bool = True
        outer: Node = self.head
        inner: Node = self.tail
        while outer != self.tail:
            inner = self.tail
            while inner != outer:
                if inner.key < inner.prev.key:
                    k = inner.key
                    inner.key = inner.prev.key
                    inner.prev.key = k
                inner = inner.prev
            outer = outer.next
```