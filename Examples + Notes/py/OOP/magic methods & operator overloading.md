-   magic methods
    -   basics
        
        special methods which have **double underscores** at the beginning and end of their names.
        
        they are also known as **dunders**.
        
        **init** is magic method for creating an instance.
        
        used to create functionality that can't be represented as a normal method.
        
        one common use is **operator overloading**.
        
        this means defining operators for custom classes that allow operators such as + and \* to be used on them.
        
        an example magic method is **add** for +
        
        ```python
        class Vector2D:
        	def __init__(self, x, y):
        		self.x = x
        		self.y = y
        	def __add__(self, other):
        		return Vector2D(self.x + other.x, self.y + other.y)
        
        first = Vector2D(5, 7)
        second = Vector2D(3, 9)
        result = first + second
        print(result.x)
        print(result.y)
        ```
        
        the **add** method allows for the definition of a custom behavior for the + operator in the class.
        
        it adds the corresponding attributes of the objects and returns a new object, containing the result.
        
        once it's defined, we can add 2 objects of the class together.
        
    -   more methods(for operations)
        
        -   **sub** for -
        -   **mul** for \*
        -   **truediv** for /
        -   **floordiv** for //
        -   **mod** for %
        -   **pow** for \*\*
        -   **and** for &
        -   **xor** for ^
        -   **or** for |
        
        the expression **x + y** is translated to **x.**add**(y)**.
        
        however, if x hasn't implemented **add**, and x and y are of different types, then **y.**radd**(x)** is called.
        
        there are equivalent **r** methods for all magic methods just mentioned.
        
        ```python
        B().__rxor__(A())
        #abv: A() ^ B() if A doesn't implement any magic methods
        ```
        
        ```python
        class SpecialString:
        	def __init__(self, cont):
        		self.cont = cont
        
        	def __truediv__(self, other):
        		line = "=" * len(other.cont)
        		return "\\n".join([self.cont, line, other.cont])
        
        spam = SpecialString("spam")
        hello = SpecialString("Hello World!")
        print(spam / hello)
        ```
        
        in the example above, the **division** operation is defined for the class **SpecialString**.
        
    -   more methods(for comparisons)
        
        -   **lt** for <
        -   **le** for ≤
        -   **eq** for ==
        -   **ne** for ≠
        -   **gt** for >
        -   **ge** for ≥
        
        if **ne** is not implemented, it returns the opposite of **eq**
        
        there are no other relationships between the other operators.
        
        ```python
        class SpecialString:
        	def __init__(self, cont):
        		self.cont = cont
        
        	def __gt__(self, other):
        		for index in range(len(other.cont) + 1):
        			result = other.cont[:index] + ">" + self.cont
        			result += ">" + other.cont[index:]
        
        spam = SpecialString("spam"
        eggs = SpecialString("eggs")
        spam > eggs
        ```
        
        as seen abv, you can define any custom behavior for the overloaded operators.
        
    -   more methods(for making classes act like containers)
        
        -   **len** for len()
        -   **getitem** for indexing
        -   **setitem** for assigning to indexed values
        -   **delitem** for deleting indexed values
        -   **iter** for iteration over objects(i.e. in for loops)
        -   **contains** for in
        
        there are many other magic methods, like **call** for calling objects, and **int**, **str**, and the like, for converting objects to built-in types.
        
        ```python
        import random
        
        class VagueList:
        	def __init__(self, cont):
        		self.cont = cont
        
        	def __getitem__(self, index):
        		return self.cont[index + random.randint(-1, 1)]
        	
        	def __len__(self):
        		return random.randint(0, len(self.cont) * 2)
        
        vague_list = VagueList(["A", "B", "C", "D", "E"])
        print(len(vague_list))
        print(len(vague_list))
        print(vague_list[2])
        print(vague_list[2])
        ```
        
        abv, we have overridden the len() function for the class VagueList to return a random number.
        
        the indexing function also returns a random item in a range from the list, based on the expression.
        
        ```python
        x.__setitem__(y, z)
        #is the magic method call made by x[y] = z
        ```