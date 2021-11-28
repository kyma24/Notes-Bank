-   basics - what it is, syntax
    
    two paradigms of programming:
    
    -   **imperative**(using statements, loops, and functions as subroutines)
    -   **functional**(using pure functions, higher-order functions, and recursion)
    
    another very popular paradigm is object-oriented programming. Objects are created using classes, which are actually the focal point of OOP
    
    the class describes what the object will be, but is separate from the object itself. in other words, a class can be described as an object's blueprint, description, or definition
    
    classes are created using the keyword **class** and an indented block, which contains class **methods**(functions).
    
    ```python
    #i.e. simple class
    
    class Cat:
    	def __init__(self, color, legs):
    		self.color = color
    		self.legs
    
    felix = Cat("ginger", 4)
    rover = Cat("dog-colored", 4)
    stumpy = Cat("brown", 3)
    ```
    
    abv code defines class named **Cat**, which has 2 attributes: **color** and **legs**
    
    then the class is used to create 3 separate objects of that class(felix, rover, and stumpy)
    
-   **init**
    
    the ****init**** method is the most important method in a class
    
    this is called when an **instance(object)** of the class is created, using the class name as the function
    
    all methods must have **self** as their first parameter, although it isn't explicitly passed, Python adds the **self** argument to the list for you; you don't need to include it when you call the methods. Within a method definition, **self** refers to the instance calling the method.
    
    instances of classes have **attributes**, which are pieces of data associated w/ them.
    
    in the example, **Cat** instances have attributes **color** and **legs**. These can be accessed by putting a dot, and the attribute name after an instance. In an **init** method, **self.attribute** can therefor be used to set the initial value of an instance's attributes.
    
    ```python
    class Cat:
    	def __init__(self, color, legs):
    		self.color = color
    		self.legs = legs
    
    felix = Cat("ginger", 4)
    print(felix.color)
    ```
    
    in example, the **init** method takes 2 arguments and assigns them to the object's attributes. The **init** \*\*\*\*method is called the class **constructor**
    
-   methods
    
    classes can have other methods defined to add functionality to them.
    
    remember that all methods must have **self** as their first parameter. These methods are accessed using the same dot syntax as attributes.
    
    ```python
    class Dog:
    	def __init__(self, name, color):
    		self.name = name
    		self.color = color
    	
    	def bark(self):
    		print("Woof!")
    
    fido = Dog("Fido", "brown")
    print(fido.name)
    fido.bark()
    ```
    
    ```python
    #i.e.
    class Student:
    	def __init__(self, name):
    		self.name = name
    		
    		def sayHi(self):
    			print("Hi from" + self.name)
    
    s1 = Student("Amy")
    s1.sayHi()
    ```
    
-   class attributes
    
    classes can also have **class attributes**, created by assigning variables within the body of the class. These can be accessed either from instances of the class, or the class itself.
    
    ```python
    class Dog:
    	**legs = 4**
    	def __init__(self, name, color):
    		self.name = name
    		self.color = color
    
    fido = Dog("Fido", "brown")
    **print(fido.legs)
    print(Dog.legs)**
    ```
    
    note: class attributes are shared by all instances of the class.
    
    trying to access an attribute of an instance that isn't defined causes an **AttributeError**. This also applies when you call an undefined method
    
    ```python
    class Rectangle:
    	def __init__(self, width, height):
    		self.width = width
    		self.height = height
    
    rect = Rectangle(7, 8)
    print(rect.color)
    ```