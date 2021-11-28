Main operations:
- `add(element)` adds element to the set. Will not have any effect if element is already in the set
- `remove(element)` removes element from the set. Will not have any effect if element is not present in the set
- `contains(element)` returns `True` if element is in the set, `False` otherwise
- `__iter__(element)` allows to iterate over elements of the set(in an unspecified order)

Main benefit of sets is that time complexity of `add`, `remove`, and `contains` are all **constant time** operations.

Can implement set based on resizeable array: assume that we are putting values into an array and at some point there is no more room for new elements. To solve this problem, we can make the initial array big enough that it will never run out of space. However, as the number of elements change over time we waste a lot of memory when the array is almost empty. Resizeable arrays make the array larger when it is running out of space and smaller when it has a lot of free space.
```python
class ResizableArray:

    # ratio of element to size of array on witch it should be downsized
    RESIZE_FACTOR_UP = 1/2
    # ratio of element to size of array on witch it should be upsized
    RESIZE_FACTOR_DOWN = 1/3
    # minimal size of the array (the size is not shrinked below this size)
    MIN_SIZE = 10

    def __init__(self, size=10):
        self._size = size
        # current amount of the elements in array
        self._filled = 0
        # initialize and prepopulate list of length size given in constructor
        self._element = [None for _ in range(size)]

    def contains(self, value):
        for e in self._element:
            if e == value:
                return True
        return False

    def add(self, value):
        # increment amount of element if you add new element
        if not self.contains(value):
            for i, v in enumerate(self._element):
                # find first empty place in underlying array
                if not v:
                    self._element[i] = value
                    break
            self._filled += 1
            self._resize()

    def delete(self, value):
        # decrement amount of elements if you remove element that existed
        if self.contains(value):
            self._filled -= 1

            for i, v in enumerate(self._element):
                if v == value:
                    self._element[i] = None
                    break
            self._resize()

    # resize array if there is to much or not enougth free space
    def _resize(self):
        capacity_ratio = float(self._filled) / self._size
        # shrink array if there is less than RESIZE_FACTOR_DOWN elements
        if capacity_ratio < ResizableArray.RESIZE_FACTOR_DOWN and self._size / 2 >= ResizableArray.MIN_SIZE:
            new_element_array = [None for _ in range(int(self._size/2))]
            i = 0
            for e in self._element:
                if e:
                    new_element_array[i] = e
                    i += 1
            self._element = new_element_array
            self._size = len(new_element_array)
        # grow arrary if there is more than then RESIZE_FACTOR_UP elements
        if capacity_ratio > ResizableArray.RESIZE_FACTOR_UP:
            for i in range(self._size):
                self._element.append(None)
            self._size *= 2

    def __str__(self):
        return f"size: {self._size} elements: {self._element}"
```

The final interpretation utilizes a hash function to indice the values.
```python
class Set:

    # ratio of element to size of array on witch it should be downsized
    RESIZE_FACTOR_UP = 1/2
    # ratio of element to size of array on witch it should be upsized
    RESIZE_FACTOR_DOWN = 1/3
    # minimal size of the array (the size is not shrinked below this size)
    MIN_SIZE = 10

    def __init__(self, size=10):
        self._size = size
        # # initialize hashing function
        # self._hash_function = lambda x: hash(x) % self._size
        # current amount of the elements in array
        self._filled = 0
        # initialize and prepopulate list of length size given in constructor
        self._element = [[] for _ in range(size)]

    def _hash_function(self, value):
        return hash(value) % self._size

    def _contains(self, value):
        for i, e in enumerate(self._element[self._hash_function(value)]):
            if value == e: return i
        return -1

    def contains(self, value):
        return self._contains(value) >= 0

    def add(self, value):
        if not self.contains(value):
            self._filled += 1
        self._element[self._hash_function(value)].append(value)
        self._resize()

    def delete(self, value):
        # decrement amount of elements if you remove element that existed
        index = self._contains(value)
        if index >= 0:
            self._filled -= 1
            self._element[self._hash_function(value)].pop(index)
            self._resize()

    # resize array if there is to much or not enougth free space
    def _resize(self):
        capacity_ratio = float(self._filled) / self._size
        # shrink array if there is less than RESIZE_FACTOR_DOWN elements
        if capacity_ratio < Set.RESIZE_FACTOR_DOWN and self._size / 2 >= Set.MIN_SIZE:
            self._create_resized_array(self._size/2)
        # grow array if there is more than then RESIZE_FACTOR_UP elements
        if capacity_ratio > Set.RESIZE_FACTOR_UP:
            self._create_resized_array(self._size * 2)

    def _create_resized_array(self, new_size):
        new_element_array = [[] for _ in range(int(new_size))]
        self._size = len(new_element_array)
        for l in self._element:
            for e in l:
                # uses new function
                new_element_array[self._hash_function(e)].append(e)
        self._element = new_element_array

    def __iter__(self):
        for l in self._element:
            if l:
                for e in l:
                    yield e
        raise StopIteration()

    def __str__(self):
        return f"size: {self._size} elements: {self._element}"
```