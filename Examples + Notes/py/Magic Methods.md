-   intro
    
    -   "everything" in object oriented Python
    -   special methods that are defined to add "magic" to the class
    -   always surrounded by double underscores
    -   also called dunder methods
    -   not meant to be invoked directly to user, but invocation happens internally from the class on a certain action.
-   construction & initialization
    
    most basic magic method: **init**
    
    -   the way to define the initialization behavior of object
    
    however, when call x = SomeClass(), **init** isn't the first thing to be called. The first method called is ****new****, which creates the instance, then passes any arguments at the creation onto the initializer.
    
    At the end of the object's lifespan, there's **del**.
    
    **new**(cls, \[...)
    
    -   is the first method to get called in an object's instantiation.
    -   it takes the class, then any other arguments that it will pass along to **init**.
    -   **new** used fairly rarely, but does have special purposes, particularly when subclassing an immutable type like a tuple or string.
    
    **init**(self, \[...)
    
    -   the initializer for the class
    -   gets passed whatever the primary constructor was called with(i.e. if we called x = SomeClass(10, 'foo'), **init** would get passed 10 and 'foo' as arguments)
    -   almost universally used in Python class definitions
    
    **del**(self)
    
    -   the destructor
    -   doesn't implement behavior for the statement del x(so that code won't translate to x.**del**())
    -   Defines behavior for when an object is garbage collected.
    -   can be useful for objects that might require extra cleanup upon deletion, like sockets or file objects
    -   careful: no guarantee that **del** will be executed if the object is still alive when the interpreter exits, so it can't serve as a replacement for good coding practices(like always closing a connection when ur done w/ it)
    -   this should almost never be used bc of the precarious circumstances under which it is called
    
    ```python
    #__init__ + __del__
    from os.path import join
    
    class FileObject:
    	'''wrapper for file objects to make sure the file gets closed on deletion'''
    
    	def __init__(self, filepath="~", filename = 'sample.txt'):
    	# open a file filename in filepath in read and write mode
    		self.file = open(join(filepath, filename), 'r+')
    
    	def __del__(self):
    		self.file.close()
    		del self.file
    ```
    
-   making operators work on custom classes
    
    biggest advantage of using Python magic methods is that they provide simple way to make objects behave like built-in types. Can avoid counter-intuitive/nonstandard was of performing basic operators.
    
    in some languages, common to do this:
    
    ```python
    if instance.equals(other_instance):
    	#do something
    ```
    
    could still do in Python, but adds confusion and is verbose. Diff libraries may use different names for the same operations, making the client to more work than necessary
    
    with magic methods, however, we can define 1 method(**eq** in this case), and say what is meant instead.
    
    ```python
    if instance == other_instance:
    	#do something
    ```
    
    part of the power of magic methods. Vast majority of them allow us to define meaning for operators so that we can use them on own classes just like they were built in types.
    
    -   comparison magic methods
        
        Python has many magic methods designed to implement intuitive comparisons between objects using operators. They also provide a way to override the default Python behavior for comparisons of objects.
        
        -   **cmp**(self, other)
            
            -   this is the most basic of all comparison magic methods.
            -   implements behavior for all of the comparison operators(<, ==, !=, etc) but might not be done the way wanted
                -   i.e. whether one instance was equal to another were determined by 1 criterion and whether an instance is greater than another were determined by something else)
            -   should return a negative integer if self < other, zero if self == other, and positive if self > other.
            -   \[ \] usually best to define each comparison you need rather than define all at once, but **cmp** can be a good way to save repetition and improve clarity when you need all comparisons implemented w/ similar criteria
        -   **eq**(self, other)
            
            defines behavior for equality operator, ==
            
        -   **ne**(self, other)
            
            defines behavior for inequality operator, !=
            
        -   **lt**(self, other)
            
            defines behavior for less-than operator <
            
        -   **gt**(self, other)
            
            defines behavior for greater than operator >
            
        -   **le**(self, other)
            
            defines behavior for less than or equal to operator, <=
            
        -   **ge**(self, other)
            
            defines behavior for the greater than equal to operator >=
            
        
        i.e. consider a class to model a word. Might want to compare words lexicographically(by the alphabet) which is the default comparison behavior for strings, but also might want to do it based on some other criterion, like length or # of syllables.
        
        ```python
        #comparing by length
        class Word(str):
        	'''Class for words, defining comparison based on word length'''
        
        	def __new__(cls, word):
        		# note that have to use __new__. this is bc str is immutable type, so have to initialize it early(at creation)
        
        		if '' in word:
        			print "Value contains spaces. Truncating to first space."
        			word = word[:word.index('')] #word is now all chars before first space
        		return str.__new__(cls, word)
        
        	def __gt__(self, other):
        		return len(self) > len(other)
        	def __lt__(self, other):
        		return len(self) < len(other
        	def __ge__(self, other):
        		return len(self) >= len(other)
        	def __le__(self, other):
        		return len(self) <= len(other)
        ```
        
        now can create two Word s(by using Word('foo') and Word('bar')) and compare them based on length. However, we didn't define **eq** and **ne**. This is bc this would lead to some weird behavior(Word('foo') == Word('bar') would eval to true). It wouldn't make sense to test for equality based on length, so fall back on str's implementation of equality
        
        note that don't have to define every comparison magic method to get rich comparisons. Standard library has provided w/ a class decorator in the module **functools** that will define all rich comparison methods if you only define **eq** and one other(eg. **gt**, **lt**, etc), though only available in Python 2.7(use it by placing @total\_ordering above class definition)
        
    -   numeric magic methods
        
        just like how can create ways for instances of class to be compared w/ comparison operators, can also define behavior for numeric operators.
        
        there are many, so split into 5 categories: unary operators, normal arithmetic operators, reflected arithmetic operators, augmented assignment, and type conversions
        
        -   unary operators & functions
            
            only have 1 operand e.g. negation, abs val, etc
            
            -   **pos**(self)
                
                implements behavior for unary positive(e.g. +some\_object)
                
            -   **neg**(self)
                
                implements behavior for negation(e.g. -some\_object)
                
            -   **abs**(self)
                
                implements behavior for the built in abs() function
                
            -   **invert**(self)
                
                implements behavior for inversion using ~ operator.(bitwise operations)
                
            -   **round**(self, n)
                
                implements behavior for the built in round() function. n is the number of decimal places to round to
                
            -   **floor**(self)
                
                implements behavior for math.floor(), i.e. rounding down to nearest integer
                
            -   **ceil**(self)
                
                implements behavior for math.ceil(), i.e. rounding up to nearest integer
                
            -   **trunc**(self)
                
                implements behavior for math.trunc(), i.e. truncating to an integral
                
        -   normal arithmetic operators
            
            now cover typical binary operations(and a few functions): +, =, \*, etc.
            
            -   **add**(self, other)
                
                implements addition
                
            -   **sub**(self, other)
                
                implements subtraction
                
            -   **mul**(self, other)
                
                implements multiplication
                
            -   **floordiv**(self, other)
                
                implements integer division using the // operator
                
            -   **div**(self, other)
                
                implements division using the / operator
                
            -   **truediv**(self, other)
                
                implements _true_ division. note that this only works when from **future** import division is in effect.
                
            -   **mod**(self, other)
                
                implements modulo using the % operator
                
            -   **divmod**(self, other)
                
                implements behavior for long division using the divmod() built in function
                
            -   **pow**(self, other)
                
                implements behavior for exponents using the \*\* operator
                
            -   **lshift**(self, other)
                
                implements left bitwise shift using the << operator
                
            -   **rshift**(self, other)
                
                implements right bitwise shift using >> operator
                
            -   **and**(self, other)
                
                implements bitwise and using the & operator
                
            -   **or**(self, other)
                
                implements bitwise or using the | operator
                
            -   **xor**(self, other)
                
                implements bitwise xor using the ^ operator
                
        -   reflected arithmetic operators
            
            normal addition:
            
            ```python
            some_object + other
            ```
            
            reflected addition:
            
            ```python
            other + some_object
            ```
            
            these magic methods do the same thing as normal equivalents, except perform the operation with the other as the first operand and self as the second rather than the other way round.
            
            most cases, reflected operand is same as normal equivalent, so may just end up redefining **radd** as calling **add** and so on.
            
            note that object on left hand side of operator(other in the example) must not define(or return NotImplemented) for its definition of the non-reflected version of an operation. for instance, in the example, some\_object.**radd** will only be called if other doesn't define **add**
            
            -   **radd**(self, other)
                
                implements reflected addition
                
            -   **rsub**(self, other)
                
                implements reflected subtraction
                
            -   **rmul**(self, other)
                
                implements reflected multiplication
                
            -   **rfloordiv**(self, other)
                
                implements reflected integer division using the // operator
                
            -   **rdiv**(self, other)
                
                implements reflected division using the / operator
                
            -   **rtruediv**(self, other)
                
                implements reflected _true_ division. note that this only works when **from **future** import division** is in effect.
                
            -   **rmod**(self, other)
                
                implements reflected modulo using the % operator
                
            -   **rdivmod**(self, other)
                
                implements behavior for long division using the divmod() built in function, when divmod(other, self) is called
                
            -   **rpow**(self, other)
                
                implements behavior for reflected exponents using the \*\* operator
                
            -   **rlshift**(self, other)
                
                implements reflected left bitwise shift using the << operator
                
            -   **rrshift**(self, other)
                
                implements reflected right bitwise shift using the >> operator
                
            -   **rand**(self, other)
                
                implements reflected bitwise and using the & operator
                
            -   **ror**(self, other)
                
                implements reflected bitwise or using the | operator
                
            -   **rxor**(self, other)
                
                implements reflected bitwise xor using the ^ operator
                
        -   augmented assignment
            
            also has wide variety of magic methods to allow custom behavior to be defined for augmented assignment.
            
            augmented assignment combines "normal" operators with assignment.
            
            ```python
             x = 5
            x += 1 # in other words x = x + 1
            ```
            
            each of these methods should return the value that the variable on the left hand side should be assigned to(i.e., for a += b, **iadd** might return a + b, which would be assigned to a)
            
            -   **iadd**(self, other)
                
                implements addition with assignment
                
            -   **isub**(self, other)
                
                implements subtraction with assignment
                
            -   **imul**(self, other)
                
                implements multiplication with assignment
                
            -   **ifloordiv**(self, other)
                
                implements integer division with assignment using the //= operator
                
            -   **idiv**(self, other)
                
                implements division with assignment using the /= operator
                
            -   **itruediv**(self, other)
                
                implements _true_ division with assignment. Note that this only works when **from **future** import division** is in effect
                
            -   **imod**(self, other)
                
                implements modulo with assignment using the %= operator
                
            -   **ipow**(self, other)
                
                implements behavior for exponents with assignment using the \*\*= operator
                
            -   **ilshift**(self, other)
                
                implements left bitwise shift with assignment using the <<= operator
                
            -   **irshift**(self, other)
                
                implements right bitwise shift with assignment using the >>= operator
                
            -   **iand**(self, other)
                
                implements bitwise and with assignment using the &= operator
                
            -   **ior**(self, other)
                
                implements bitwise or with assignment using the |= operator
                
            -   **ixor**(self, other)
                
                implements bitwise xor with assignment using the ^= operator
                
        -   type conversion magic methods
            
            python also has an array of magic methods designed to implement behavior for built in type conversion functions like float().
            
            -   **int**(self)
                
                implements type conversion to int.
                
            -   **long**(self)
                
                implements type conversion to long
                
            -   **float**(self)
                
                implements type conversion to float
                
            -   **complex**(self)
                
                implements type conversion to complex
                
            -   **oct**(self)
                
                implements type conversion to octal
                
            -   **hex**(self)
                
                implements type conversion to hexadecimal
                
            -   **index**(self)
                
                implements type conversion to an int when the object is used in a slice expression. If you define a custom numeric type that might be used in slicing, you should define **index**
                
            -   **trunc**(self)
                
                called when math.trunc(self) is called. **trunc** should return the value of \`self truncated to an integral type(usually a long).
                
            -   **coerce**(self, other)
                
                method to implement mixed mode arithmetic. **coerce** should return None if type conversion is impossible. Otherwise, it should return a pair(2-tuple) of self and other, manipulated to have the same type.
                

[here](https://rszalski.github.io/magicmethods/)