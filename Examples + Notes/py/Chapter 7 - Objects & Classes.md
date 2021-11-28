object-oriented programming enables you to develop large-scale software and GUIs efficiently.

-   7.2 - Defining Classes for Objects
    
    a class defines the properties and behaviors for objects.
    
    OOP involves the use of objects to create programs. An object represents an entity in the real world that can be distinctly identified. For example, a student, a desk, a circle, a button, and even a loan can all be viewed as objects. An object has a unique **identity**, **state**, and **behavior**.
    
    -   an object's _identity_ is like a person's Social Security number. Python automatically assigns each object a unique id for identifying the object at runtime.
    -   an object's _state_, also known as its _properties_ or _attributes_) is represented by variables, called _data fields_. A circle object, for example, has a data field **radius**, which is a property that characterizes a circle. A rectangle object has the data fields **width** and **height**, which are properties that characterize a rectangle.
    -   Python uses methods to define an object's _behavior_, or its _actions_. Methods are defined as functions. You make an object perform an action by invoking a method on that object. For example, you can define methods named **getArea()** and **getPerimeter()** for circle objects. A circle object can then invoke the **getArea()** method to return its area and the **getPerimeter()** method to return its circumference.
    
    Objects of the same kind are defined by using a common class. The relationship between classes and objects is analogous to that between an apple-pie recipe and the apple pies. You can make as many apple pies(objects) as you want from a single recipe(class)
    
    A Python _class_ uses variables to store data fields and defines methods to perform actions. A class is a contract— also sometimes called a _template_ or a _blueprint_— that defines what an object's data fields and methods will be.
    
    An object is an instance of a class, and you can create many instances of a class. Creating an instance of a class is referred to as _instantiation_. The terms _object_ and _instance_ are often used interchangeably. An object is an instance and an instance is an object.
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c439b391-04c1-45c8-8138-3111a87e5615/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c439b391-04c1-45c8-8138-3111a87e5615/Untitled.png)
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c6dd2c38-4dfe-4f2f-a29b-a84733614fd7/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c6dd2c38-4dfe-4f2f-a29b-a84733614fd7/Untitled.png)
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fc8bbd0f-292a-4e6b-a1ac-79d3de6645fa/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fc8bbd0f-292a-4e6b-a1ac-79d3de6645fa/Untitled.png)
    
    -   7.2.1 - Defining Classes
        
        in addition to using variables to store data fields and define methods, a class provides a special method, ****init****. This method, known as an _initializer_, is invoked to initialize a new object's state when it is created. An initializer can perform any action, but initializers are designed to perform initializing actions, such as creating an object's data fields with _initial values_.
        
        ```python
        #defining a class in Python:
        
        class ClassName:
        	initializer
        	methods
        ```
        
        [Circle.py](http://Circle.py) defines the **Circle** class. The class name is preceded by the keyword **class** and followed by a colon(**:**). The initializer is always named ****init****, which is a special method. _Note that **init** needs to be preceded and followed by two underscores._ A data field **radius** is created in the initializer. The methods **getPerimeter** and **getArea** are defined to return the perimeter and area of a circle.
        
        ```python
        import math
        
        class Circle:
        	#Construct a circle object
        	def __init__(self, radius = 1):
        		self.radius = radius
        
        	def getPerimeter(self):
        		return 2 * self.radius * math.pi
        	
        	def getArea(self):
        		return self.radius * self.radius * math.pi
        
        	def setRadius(self, radius):
        		self.radius = radius
        ```
        
    -   7.2.2 - Constructing Objects
        
        Once a class is defined, you can create objects from the class with a _constructor_. The constructor does 2 things:
        
        -   it creates an object in the memory for the class
        -   it invokes the class's ****init**** method to initialize the object.
        
        All methods, including the initializer, have the first parameter **self**. This parameter refers to the object that invokes the method. The **self** parameter in the ****init**** method is automatically set to reference the object that was just created. You can specify any name for this parameter, but by convention **self** is usually used.
        
        ```python
        #the syntax of a constructor
        
        ClassName(arguments)
        ```
        
        1.  it creates an object in the memory for the class
        2.  it invokes the class's **init** method to initialize the object. the self parameter in the **init** in the **init** method is automatically set to reference the object that was just created.
        
        note: Constructing an object creates the object in the memory and invokes its initializer
        
        The arguments of the constructor match the parameters in the ****init**** method without **self**. For example, since the ****init**** method in the fifth line of [Circle.py](http://Circle.py) is defined as ****init**(self, radius = 1)**, to construct a **Circle** object with radius **5**, you should use **Circle(5)**.
        
        First, a **Circle** object is created in the memory, and then the initializer is invoked to set **radius** to **5**.
        
        The initializer in the **Circle** class has a default **radius** value of **1**. The following constructor creates a **Circle** object with a default radius of **1**:
        
        ```python
        Circle()
        ```
        
    -   7.2.3 - Accessing Members of Objects
        
        An object's member refers to its data fields and methods. Data fields are also called _instance variables_, bc each object(instance) has a specific value for a data field. Methods are also called _instance methods_, because a method is invoked by an object(instance) to perform actions on the object such as changing the values in data fields for the object. In order to access an object's data fields and invoke an object's methods, you need to assign the object to a variable by using the following syntax:
        
        ```python
        objectRefVar = ClassName(arguments)
        ```
        
        For example,
        
        ```python
        c1 = Circle(5)
        c2 = Circle()
        ```
        
        You can access the object's data fields and invoke its methods by using the _dot operator_(.), also known as the _object member access operator_. The syntax for using the dot operator is:
        
        ```python
        objectRefVar.datafield
        objectRefVar.method(args)
        ```
        
        For example, the below code accesses the **radius** data field, and then invokes the **getPerimeter** method and the **getArea** method. Note that the first line imports the **Circle class** defined in [Circle.py](http://Circle.py).
        
        ```python
        >>> from Circle import Circle
        >>> c = Circle(5)
        >>> c.radius
        5
        >>> c.getPerimeter()
        31.41592653589793
        >>> c.getArea()
        78.53981633974483
        >>>
        ```
        
        note: usually you can create an object and assign it to a variable. Later you can use the variable to reference the object. Occasionally an object doesn't need to be referenced later. In this case, you can create an object w/o explicitly assigning it to a variable, as shown:
        
        ```python
        print("Area is", Circle(5).getArea())
        ```
        
        The statement creates a **Circle** object and invokes its **getArea** method to return its area. An object created in this way is known as an _anonymous object_.
        
    -   7.2.4 - the **self** parameter
        
        as mentioned in the past, the first parameter for each method defined is **self**. This parameter is used in the implementation of the method, but it isn't used when the method is called. So what is this parameter for, and why do we need it?
        
        **self** is a parameter that references the object itself. Using **self**, you can access objects' members in a class definition. For example, you can use the syntax **self.x** to access the instance variable **x** and the syntax **self.m1()** to invoke the instance method **m1** for the object **self** in a class.
        
        ```python
        def ClassName:
        	
        	def __init__(self, ...):
        		self.x = 1 #Create/modify x
        		...
        
        	def m1(self, ...):
        		self.y = 2 #Create/modify y
        		...
        		z = 5 #Create/modify z
        		...
        
        	def m2(self, ...):
        		self.y = 3 #Create/modify y
        		...
        		u = self.x + 1 #Create/modify u
        		self.m1(...) #Invoke m1
        
        Green - scope of self.x and self.y(all of code)
        Blue - scope of z
        ```
        
        the scope of an instance variable is the entire class one it is created. Above, **self.x** is an instance variable created in the ****init**** method. It is accessed in method **m2**. The instance variable **self.y** is set to **2** in method **m1** and set to **3** in **m2**. Note that you can also create local variables in a method. The scope of a local variable(like **z**) is within the method. The local variable **z** is created in method **m1** and its scope is from its creation to the end of method **m1**.
        
    -   7.2.5 - Example: Using Classes
        
        This section presents a test program that constructs three circle objects with radii of **1**, **25**, and **125**, and then displays the radius and area of each circle in the following [TestCircle.py](http://TestCircle.py). The program then changes the radius of the second object to **100** and displays its new radius and area.
        
        ```python
        #Circle file
        import math
        
        class Circle:
        	#Construct a circle object
        	def __init__(self, radius = 1):
        		self.radius = radius
        
        	def getPerimeter(self):
        		return 2 * self.radius * math.pi
        	
        	def getArea(self):
        		return self.radius * self.radius * math.pi
        
        	def setRadius(self, radius):
        		self.radius = radius
        ```
        
        ```python
        from Circle import Circle
        
        def main():
        	#Create a circle with radius 1
        	circle1 = Circle()
        	print("The area of the circle of radius", circle1.radius, "is", circle1.getArea())
        
        	#Create a circle with radius 25
        	circle2 = Circle(25)
        	print("The area of the circle of radius", circle2.radius, "is", circle2.getArea())
        
        	#Create a circle with radius 125
        	circle 3 = Circle(125)
        	print("The area of the circle of radius", circle3.radius, "is", circle3.getArea())
        
        	#Modify circle radius
        	circle2.radius = 100 # or circle2.setRadius(100)
        	print("The area of the circle of radius", circle2.radius, "is", circle2.getArea())
        
        main() #call the main function
        ```
        
        ```python
        The area of the circle of radius 1.0 is 3.141592653589793
        The area of the circle of radius 25.0 is 1963.4954084936207
        The area of the circle of radius 125.0 is 49087.385212340516
        The area of the circle of radius 100.0 is 31415.926535897932
        ```
        
        The program uses the **Circle** class to create **Circle** objects. Such a program that uses the class(such as **Circle**) is often referred to as a _client_ of the class.
        
        The **Circle** class is imported in line 1 using the syntax **from Circle import Circle**. The program creates a **Circle** object with a default radius **1** and creates 2 **Circle** objects with the specified radii, and then retrieves the **radius** property and invokes the **getArea()** method on the objects to obtain the area. The program sets a new **radius** property on **circle2**. This can also be done by using **circle2.setRadius(100)**.
        
        note: a variable that appears to hold an object actually contains a reference to that object. Strictly speaking, a variable and an object are different, but most of the time the distinction can be ignored, so it is fine, for simplicity, to say that "**circle1** is a **Circle** object" rather than use the longer-winded description that "**circle1** is a variable that contains a reference to a **Circle** object"
        
    -   Reflection Questions
        
        -   7.1 Describe the relationship between an object and its defining class.
            
            An object is an instance of a class, where you can create as many as necessary. The class defines the object's identity, attributes, and behavior; in other words, the class is the blueprint of the subsequent object.
            
        -   7.2 How do you define a class?
            
            ```python
            class ClassName:
            	#initializer
            
            	#methods
            ```
            
        -   7.3 How do you create an object?
            
            ```python
            ObjectName(arguments):
            	#content
            ```
            
        -   7.4 What is the name of the initializer method?
            
            **init**
            
        -   7.5 The first parameter in the initializer method is named **self** by convention. What is the role of **self**?
            
            self is the parameter that references the object itself. Using it, you can access the object's methods in a class definition.
            
        -   7.6 What is the syntax for constructing an object? What does Python do when constructing an object?
            
        -   7.7 What are the differences between an initializer and a method?
            
        -   7.8 What is the object member access operator for?
            
        -   7.9 What problem arises in the following program? How do you fix it?
            
            ```python
            class A:
            	def __init__(self, i):
            		self.i = i
            
            def main():
            	a = A()
            	print(a.i)
            
            main() # Call the main function
            ```
            
        -   7.10 What is wrong with the following programs?
            
            ```python
            #a
            class A:
            	#Construct an object of the class
            	def A(self):
            		radius = 3
            ```
            
            ```python
            #b
            class A:
            	#Construct an object of the class
            	def __init__(self);
            		radius = 3
            	
            	def setRadius(radius):
            		self.radius = radius
            ```
            
-   7.3 - UML Class Diagrams
    
    UML(Unified Modeling Language) class diagrams use graphical notation to describe classes. This notation is called a _UML class diagram_ or simply a _class diagram_, and is language independent; that is, other programming languages use this same modeling and notation.
    
    In UML class diagrams, data fields are denoted as:
    
    ```python
    dataFieldName: dataFieldType
    ```
    
    Constructors are shown as:
    
    ```python
    ClassName(parameterName: parameterType)
    ```
    
    Methods are represented as:
    
    ```python
    methodName(parameterName: parameterType): returnType
    ```
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ebf8aa00-5683-458c-af4c-dd3f6b17a0cc/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ebf8aa00-5683-458c-af4c-dd3f6b17a0cc/Untitled.png)
    
    The method definition in the class always has the special **self** parameter, but isn't included in the UML diagram, because the client doesn't need to know this parameter and doesn't use this parameter to invoke the methods.
    
    The ****init**** method also doesn't need to be listed in the UML diagram, because it's invoked by the constructor and its parameters are the same as the constructor's parameters.
    
    The UML diagram serves as the contract(template) for the client so that it will know how to use the class. The diagram describes for the client how to create objects and how to invoke the methods on the objects.
    
    As an example, consider TV sets. Each TV is an object with states(that is, current channel, current volume level, and power on or off are its properties that are represented by data fields) and behaviors(change channels, adjust volume, and turn on/off are the actions each TV object implements with methods). You can use a class to define TV sets. The UML diagram for the **TV** class is shown.
    
    **TV**
    
    channel: int ← the current channel(1-120) of this TV
    
    volumeLevel: int ← the current volume level(1-7) of this TV
    
    on: bool ← Indicates whether this TV is on/off
    
    ---
    
    TV() ← Constructs a default TV object
    
    turnOn(): None ← turns on this TV
    
    turnOff(): None ← turns off this TV
    
    getChannel(): int ← returns the channel for this TV
    
    setChannel(channel: int): None ← sets a new channel for this TV
    
    getVolume(): int ← gets the volume level for this TV
    
    setVolume(volumeLevel: int): None ← sets a new volume level for this TV
    
    channelUp(): None ← increases the channel number by 1
    
    channelDown(): None ← decreases the channel number by 1
    
    volumeUp(): None ← increases the volume level by 1
    
    volumeDown(): None ← decreases the volume level by 1
    
    ```python
    #Python code for TV class
    class TV:
    	def __init__(self):
    		self.channel = 1 # default channel is 1
    		self.volumeLevel = 1 # default volume level is 1
    		self.on = False # TV is initially off
    
    	def turnOn(self):
    		self.on = True
    
    	def turnOff(self):
    		self.on = False
    	
    	def getChannel(self):
    		return self.channel
    
    	def setChannel(self, channel):
    		if self.on and 1 <= self.channel <= 120:
    			self.channel = channel
    
    	def getVolumeLevel(self):
    		return self.volumeLevel
    
    	def setVolume(self, volumeLevel):
    		if self.on and \\ 1 <= self.volumeLevel <= 7:
    			self.volumeLevel = volumeLevel
    
    	def channelUp(self):
    		if self.on and self.channel < 120:
    			self.channel += 1
    
    	def channelDown(self):
    		if self.on and self.channel > 1:
    			self.channel -= 1
    
    	def volumeUp(self):
    		if self.on and self.volumeLevel < 7:
    			self.volumeLevel += 1
    
    	def volumeDown(self):
    		if self.on and self.volumeLevel > 1:
    			self.volumeLevel -= 1
    ```
    
    the initializer creates the instance variables **channel**, **volumeLevel**, and **on** for the data fields in a **TV** object. Note that this initializer doesn't have any argument except **self**.
    
    the channel and volume level are not changed if the TV is not on. Before either of these are changed, its current value is checked to ensure that it is within the correct range.
    
    [TestTV.py](http://TestTV.py) is a program that uses the **TV** class to create two objects.
    
    ```python
    from TV import TV
    
    def main():
    	tv1 = TV()
    	tv1.turnOn()
    	tv1.setChannel(30)
    	tv1.setVolume(3)
    
    	tv2 = TV()
    	tv2.turnOn()
    	tv2.channelUp()
    	tv2.channelUp()
    	tv2.volumeUp()
    
    	print("tv1's channel is", tv1.getChannel(),
    					"and volume level is", tv1.getVolumeLevel())
    	print("tv2's channel is", tv2.getChannel(),
    					"and volume level is", tv2.getVolumeLevel())
    
    main() # call the main function
    
    >>>
    tv1's channel is 30 and volume level is 3
    tv2's channel is 3 and volume level is 2
    >>>
    ```
    
    the program creates two **TV** objects **tv1** and **tv2**, and invokes the methods on the objects to perform actions for setting channels and volume levels and for increasing channels & volumes. **tv1** is turned on by invoking **tv1.turnOn()** in the fifth line, its channel is set to **30** by invoking **tv1.setChannel(30)** in the sixth line, and its volume level is set to **3** in the seventh line. **tv2** is turned on in the tenth line, its channel is increased by **1** by invoking **tv2.channelUp()** in the eleventh line, and again by another **1** in the twelfth line. Since the initial channel is set to **1**, **tv2**'s channel is now **3**. **tv2**'s volume is increased by **1** by invoking **tv2.volumeUp()** in the thirteenth line. Since the initial volume is set to **1**, **tv2**'s volume is now **2**.
    
    the program displays the state of the objects in the lines 15-18. The data fields are read using the **getChannel()** and **getVolume()** methods.
    
-   7.4 - Immutable Objects vs. Mutable Objects
    
    Numbers and Strings are immutable objects in Python, meaning that their contents cannot be changed. When passing an immutable object to a function, the object will not be changed.
    
    However, if you pass a mutable object into a function, the contents of the object may change.
    
    ```python
    #demonstration of the differences btwn an immutable object and mutable object arguments in a function
    from Circle import Circle
    
    def main():
    	# create a Circle object with radius 1
    	myCircle = Circle()
    	
    	# print areas for radius 1, 2, 3, 4, and 5
    	n = 5
    	printAreas(myCircle, n)
    	
    	# display myCircle.radius and times
    	print("\\nRadius is", myCircle.radius)
    	print("n is", n)
    
    def printAreas(c, times):
    	print("Radius \\t\\tArea")
    	while times >= 1:
    		print(c.radius, "\\t\\t", c.getArea())
    		c.radius = c.radius + 1
    		times = times - 1
    
    main() # call the main function
    ```
    
    -   output
        
        Radius Area
        
        1 3.141592653589793
        
        2 12.566370614359172
        
        3 29.274333882308138
        
        4 50.26548245743669
        
        5 79.53981633974483
        
        Radius is 6
        
        n is 5
        
    
    the **Circle** class is defined in [TestPassMutableObject.py](http://TestPassMutableObject.py). The program passes a **Circle** object **myCircle** and an **int** object **n** to invoke **printAreas(myCircle, n)**, which prints a table of areas for radii **1**, **2**, **3**, **4**, and **5**, as shown in the output.
    
    When you pass an object to a function, the reference of the object is passed to the function. However, there are important differences between passing immutable objects and mutable objects.
    
    -   for an argument of an immutable object such as a number or string, the original value of the object outside the function is not changed.
    -   for an argument of a mutable object such as a circle, the original value of the object is changed if the contents of the object are changed inside the function.
    
    the **radius** property of the **Circle** object **c** is incremented by **1**. **c.radius + 1** creates a new **int** object, which is assigned to **c.radius**. **myCircle** and **c** both point to the same object. When the **printAreas** function is finished, **c.radius** is **6**. So, the printout for **myCircle.radius** is **6**.
    
    **times - 1** creates a new **int** object, which is assigned to **times**. Outside of the **printAreas** function, **n** is still **5**. So, the printout for **n** is **5**.
    
    -   sample problems
        
        7.11 show the output of the following program:
        
        ```python
        class Count:
        	def __init__(self, count = 0):
        		self.count = count
        
        def main():
        	c = Count()
        	times = 0
        	for i in range(100):
        		increment(c, times)
        	
        	print("count is", c.count)
        	print("times is", times)
        
        def increment(c, times):
        	c.count += 1
        	times += 1
        
        main # call the main function
        ```
        
        7.12 show the output of the following program:
        
        ```python
        class Count:
        	def __init__(self, count = 0):
        		self.count = count
        
        def main():
        	c = Count()
        	n = 1
        	m(c, n)
        
        	print("count is", c.count)
        	print("n is", n)
        
        def m(c, n):
        	c = Count(5)
        	n = 3
        ```
        
-   7.5 - Hiding Data Fields
    
    making data fields private protects data and makes the class easy to maintain.
    
    You can access data fields via instance variables directly from an object. For example, in the following code, which lets you access the circle's radius from **c.radius**, is legal:
    
    ```python
    >>> c = Circle(5)
    >>> c.radius = 5.4 # access instance variable directly
    >>> print(c.radius) # access instance variable directly
    5.4
    >>>
    ```
    
    However, direct access of a data field in an object is not a good practice for 2 reasons:
    
    -   first, data may be tampered with. For example, **channel** in the **TV** class has a value between **1** and **120**, but it may be mistakenly set to an arbitrary value(e.g. **tv1.channel = 125**)
    -   second, the class becomes difficult to maintain and vulnerable to bugs. Suppose you want to modify the **Circle** class to ensure that the radius is nonnegative after other programs have already used the class. You have to change not only the **Circle** class but also the programs that use it, because the clients may have modified the radius directly(e.g. **myCircle.radius = -5**)
    
    to prevent direct modifications of data fields, don't let the client directly access data fields. This is known as _data hiding_. This can be done by defining _private data fields_. In Python, the private data fields are defined with two leading underscores. You can also define a _private method_ named with two leading underscores.
    
    private data fields and methods can be accessed within a class, but they cannot be accessed outside the class. To make a data field accessible for the client, provide a _get_ method to return its value. To enable a data field to be modified, provide a _set_ method to set a new value.
    
    colloquially, a **get** method is referred to as a _getter_(or _accessor_) and a **set** method is referred to as a _setter_(or _mutator_).
    
    A **get** method has the following header:
    
    ```python
    def get*PropertyName*(self):
    ```
    
    If the return type is Boolean, the **get** method is defined as follows by convention:
    
    ```python
    def is*PropertyName*(self):
    ```
    
    A **set** method has the following header:
    
    ```python
    def set*Propertyname*(*self, propertyValue*):
    ```
    
    The following code revises the **Circle** class by defining the **radius** property as private by placing two underscores in front of the property name.
    
    ```python
    #CircleWithPrivateRadius.py
    
    import math
    
    class Circle:
    	# construct a circle object
    	def __init__(self, radius = 1):
    		self.__radius = radius
    	
    	def getRadius(self):
    		return self.__radius
    
    	def getPerimeter(self):
    		return 2 * self.__radius * math.pi
    
    	def getArea(self):
    		return self.__radius * self.__radius * math.pi
    ```
    
    the **radius** property can't be directly accessed in this new **Circle** class. However, you can read it by using the **getRadius()** method.
    
    ```python
    >>> from CircleWithPrivateRadius import Circle
    >>> c = Circle(5)
    >>> c.__radius
    AttributeError: no attribute '__radius'
    >>> c.getRadius()
    5
    >>>
    ```
    
    the first line imports the **Circle** class, which is defined in the **CircleWithPrivateRadius** module above. The second line creates a **Circle** object. The third line attempts to access the property **\_\_radius**. This causes an error, because **\_\_radius** is private. However, you can use the **getRadius()** method to return the **radius**.
    
    ### 👉🏼 Tip
    
    if a class is designed for other programs to use, to prevent data from being tampered with and to make the class easy to maintain, define data fields as private. If a class is only used internally by your own program, there is no need to hide the data fields.
    
    ### 👉🏼 Note
    
    Name private data fields and methods with two leading underscores, but don't end the name with more. The names with two leading underscores and two ending underscores have a special meaning in Python. For example, **\_\_radius** is a private data field, but ****radius**** is not a private data field.
    
    -   sample problems
        
        7.13 What problem arises in running the following program? How do you fix it?
        
        ```python
        class A:
        	def __init__(self, i):
        		self.__i = i
        
        	def main():
        		a = A(5)
        		print(a.__i)
        
        main() # call the main function
        ```
        
        7.14 Is the following code correct? If so, what is the printout?
        
        ```python
        def main()
        	a = A()
        	a.print()
        
        class A:
        	def __init__(self, newS = "Welcome"):
        		self.__s = newS
        
        	def print(self):
        		print(self.__s)
        
        main() # call the main function
        ```
        
        7.15 Is the following code correct? If not, fix the error.
        
        ```python
        class A:
        	def __init__(self, on):
        		self.__on = not on
        
        def main():
        	a = A(False)
        	print(a.on)
        
        main() #call the main function
        ```
        
        7.16 What are the benefits of data hiding? How is it done in Python?
        
        7.17 How do you define a private method?
        
-   7.6 - Class Abstraction and Encapsulation
    
    _class abstraction is a concept that separates class implementation from the use of a class. The class implementation details are invisible from the user. This is known as class encapsulation._