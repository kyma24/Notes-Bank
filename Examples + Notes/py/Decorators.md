decorators provide a simple syntax for calling higher-order functions.

Higher-order functions are functions that do at least one of the following:

-   takes one or more functions as arguments(i.e. procedural parameters)
-   returns a function as its result

all other functions are _first-order functions_.

by definition, a decorator is a function that takes another function and extends the behavior of the latter function w/o explicitly modifying it.

-   functions
    
    before you can understand decorators, must first understand how functions work. In this case, **a function returns a value based on the given arguments**.
    
    ```python
    #i.e.
    >>> def add_one(number);
    ...			return number + 1
    
    >>> add_one(2)
    3
    ```
    
    In general, functions in Python may also have side effects rather than just turning an input into an output. The print() function is an example of this: it returns None while having the side effect of outputting something to the console. However, to understand decorators, it is enough to think about functions as something that turns given arguments into a value.
    
    Note: in functional programming, you work (almost) only with pure functions without side effects. While not a purely functional language, Python supports many of the functional programming concepts, including functions as first-class objects.
    
    -   first-class objects
        
        in Python, functions are first-class objects. This means that **functions can be passed around and used as arguments**, just like any other object(string, int, float, list, and so on).
        
        ```python
        def say_hello(name):
        	return f"Hello {name}"
        	
        def be_awesome(name):
        	return f"Yo {name}, together we are the awesomest!"
        
        def greet_bob(greeter_func):
        	return greeter_func("Bob")
        ```
        
        Here, say\_hello() and be\_awesome() are regular functions that expect a name given as a string. The greet\_bob() function however, expects a function as its argument. We can, for instance, pass it the say\_hello() or the be\_awesome() function:
        
        ```python
        >>> greet_bob(say_hello)
        'Hello Bob'
        
        >>> greet_bob(be_awesome)
        'Yo Bob, together we are the awesomest!'
        ```
        
        Note that greet\_bob(say\_hello) refers to 2 functions, but in different ways: greet\_bob() and say\_hello. The say\_hello function is named without parentheses. This means that only a reference to the function is passed. The function isn't executed. The greet\_bob() function, on the other hand, is written with parentheses, so it will be called as usual.
        
    -   inner functions
        
        it's possible to define functions inside other functions. Such functions are called inner functions. Here's an example of a function w/ two inner functions:
        
        ```python
        def parent():
        	print("printing from the parent() function")
        
        	def first_child():
        		print("printing from the first_child() function")
        
        	def second_child():
        		print("printing from the second_child() function")
        
        	second_child()
        	first_child()
        ```
        
        So, when you call the parent function, the output will be:
        
        ```bash
        >>> parent()
        printing from the parent() function
        printing from the second_child() function
        printing from the first_child() function
        ```
        
        note that the order in which the inner functions are defined does not matter. Like w/ any other functions, the printing only happens when the inner functions are executed.
        
        furthermore, the inner functions aren't defined until the parent function is called. They are locally scoped to parent(): they only exist inside the parent() function as local variables. Try calling first\_child(). There will be an error:
        
        ```bash
        Traceback (most recent call last):
        	File "<stdin>", line 1, in <module>
        NameError: name 'first_child' is not defined
        ```
        
        Whenever **parent()** is called, the inner functions **first\_child()** and **second\_child()** are also called. But bc of their local scope, they aren't available outside of the parent function.
        
    -   returning functions from functions
        
        Python also allows you to use functions as return values. The following example returns one of the inner functions from the outer **parent()** function:
        
        ```python
        def parent(num):
        	def first_child():
        		return "Hi, I am Emma"
        
        	def second_child():
        		return "Call me Liam"
        
        	if num == 1:
        		return first_child
        	else:
        		return second_child
        ```
        
        note that **first\_child** is returned without parentheses. Recall that this means that you are **returning a reference to the function** first\_child. In contrast first\_child() with parentheses refers to the result of evaluating the function. This can be seen in the following example:
        
        ```python
        >>> first = parent(1)
        >>> second = parent(2)
        
        >>> first
        <function parent.<locals>.first_child at 0x7f599f1e2e18>
        
        >>> second
        <function parent.<locals>.second_child at 0x7f599dad5268>
        ```
        
        this output simply emans that the first variable refers to the local first\_child() function instead of parent(), while second points to second\_child()
        
        you can now use first and second as if they are regular functions, even though the functions they point to can't be accessed directly.
        
        ```python
        >>> first()
        'Hi, I am Emma'
        
        >>> second()
        'Call me Liam'
        ```
        
        finally, note that in the earlier example the inner functions were executed within the parent function, for instance first\_child(). However, in the last example, the parentheses weren't added to the inner functions— first\_child— upon returning. That way, you got a reference to each function that you could call in the future.
        
-   simple decorators
    
    ```python
    def my_decorator(func):
    	def wrapper():
    		print("Something is happening before the function is called.")
    		func()
    		print("Something is happening after the function is called.")
    	return wrapper
    
    def say_whee():
    	print("Whee!")
    
    say_whee = my_decorator(say_whee)
    ```
    
    what happens when you call say\_whee():
    
    ```python
    >>> say_whee()
    Something is happening before the function is called.
    Whee!
    Something is happening after the function is called.
    ```
    
    to understand what's goin on here, look back @ the previous examples.
    
    The so-called decoration happens at the following line:
    
    ```python
    say_whee = my_decorator(say_whee)
    ```
    
    in effect, the name say\_whee now points to the wrapper() inner function. Remember that you return wrapper as a function when you call my\_decorator(say\_whee):
    
    ```python
    >>> say_whee
    <function my_decorator.<locals>.wrapper at 0x7f3c5dfd42f0>
    ```
    
    however, wrapper() has a reference to original say\_whee() as func, and calls that function between 2 calls to print()
    
    **decorators wrap a function, modifying its behavior**
    
    bc wrapper() is regular Python function, the way a decorator modifies a function can change dynamically. So as to not to disturb your neighbors, the following example will only run the decorated code during the day:
    
    ```python
    from datetime import datetime
    
    def not_during_the_night(func):
    	def wrapper():
    		if 7 <= datetime.now().hour < 22:
    			func()
    		else:
    			pass # Hush, the neighbors are asleep
    	return wrapper
    
    def say_whee():
    	print("Whee!")
    
    say_whee = not_during_the_night(say_whee)
    ```
    
    If say\_whee() is called after bedtime, nothing will happen:
    
    ```python
    >>> say_whee()
    >>>
    ```
    
    -   using decorators
        
        the way say\_whee() is decorated is a little clunky; first of all, you end up typing the name say\_whee three times. In addition, the decoration gets a bit hidden away below the definition of the function.
        
        Instead, Python allows you to **use decorators in a simpler way with the @ symbol**, sometimes called the **"pie" syntax**. The following code does the same thing as the first decorator example
        
        ```python
        def my_decorator(func):
        	def wrapper():
        		print("Something is happening before the function is called.")
        		func()
        		print("Something is happening after the function is called.")
        	return wrapper
        
        @my_decorator
        def say_whee():
        	print("Whee!")
        ```
        
        so, @my\_decorator is just an easier way of saying say\_whee = my\_decorator(say\_whee). It's how you apply a decorator to a function.
        
    -   reusing decorators
        
        recall that a decorator is just a regular Python function. All the usual tools for easy reusability are available. Let's move the decorator to its own **module** that can be used in many outer functions.
        
        Create a file called [decorators.py](http://decorators.py) w/ the following content:
        
        ```python
        def do_twice(func):
        	def wrapper_do_twice():
        		func()
        		func() 
        	return wrapper_do_twice
        ```
        
        note: can name inner function whatever wanted, and a generic name like wrapper() is usually okay.
        
        can now use this new decorator in other files by doing a regular import:
        
        ```python
        from decorators import do_twice
        
        @do_twice
        def say_whee():
        	print("Whee!")
        ```
        
        when this is run, should see original say\_whee() is executed twice:
        
        ```python
        >>> say_whee()
        Whee!
        Whee!
        ```
        
    -   decorating functions w/ arguments
        
        say that there is a function that accepts some arguments. Can it still be decorated?
        
        ```python
        #let's try
        from decorators import do_twice
        
        @do_twice
        def greet(name):
        	print(f"Hello {name}")
        ```
        
        unfortunately, this raises an error:
        
        ```python
        >>> greet("World")
        Traceback (most recent call last):
        	File "<stdin>", line 1, in <module>
        TypeError: wrapper_do_twice() takes 0 peositional arguments but 1 was given
        ```
        
        the problem is that the inner function wrapper\_do\_twice() doesn't take any arguments, but name="World" was passed to it. It could be fixed by letting wrapper\_do\_twice() accept 1 argument, but then it wouldn't work for the say\_whee() function created earlier.
        
        the solution is to use \*args and \*\*kwargs in the inner wrapper function. Then it will accept an arbitrary number of positional and keyword arguments. Rewrite [decorators.py](http://decorators.py) as follows:
        
        ```python
        def do_twice(func):
        	def wrapper_do_twice(*args, **kwargs):
        	func(*args, **kwargs)
        	func(*args, **kwargs)
        	return wrapper_do_twice
        ```
        
        the wrapper\_do\_twice() inner function now accepts any number of arguments and passes them on to the function it decorates. Now both the say\_whee() and greet() examples work:
        
        ```python
        >>> say_whee()
        Whee!
        Whee!
        
        >>> greet("World")
        Hello World
        Hello World
        ```
        
    -   returning values from decorated functions
        
        what happens to the return value of decorated functions? That's up to the decorator to decide.
        
        ```python
        from decorators import do_twice
        
        @do_twice
        def return_greeting(name):
        	print("Creating greeting")
        	return f"Hi {name}"
        ```
        
        try to use it:
        
        ```python
        >>> hi_adam = return_greeting("Adam")
        Creating greeting
        Creating greeting
        >>> print(hi_adam)
        None
        ```
        
        oops, the decorator ate the return value from the function.
        
        bc the do\_twice\_wrapper() doesn't explicitly return a value, the call return\_greeting("Adam") ended up returning None.
        
        to fix this, you need to **make sure the wrapper function returns the return value of the decorated function**. To do this, change the [decorators.py](http://decorators.py) file:
        
        ```python
        def do_twice(func):
        	def wrapper_do_twice(*args, **kwargs):
        		func(*args, **kwargs)
        	return wrapper_do_twice
        ```
        
        the return value from the last execution of the function is returned:
        
        ```python
        >>> return_greeting("Adam")
        Creating greeting
        Creating greeting
        'Hi Adam'
        ```
        
    -   introspection
        
        a great convenience when working w/ Python, especially in the interactive shell, is its powerful introspection ability. **Introspection** is the ability of an object to know about its own attributes at runtime. For instance, a function knows its name and **documentation**:
        
        ```python
        >>> print
        <built-in function print>
        
        >>> print.__name__
        'print'
        
        >>> help(print)
        Help on built-in function print in module builtins:
        
        print(...)
        	<full help message>
        ```
        
        the introspection works for functions you define as well:
        
        ```python
        >>> say_whee
        <function do_twice.<locals>.wrapper_do_twice at 0x7f43700e52f0>
        
        >>> say_whee.__name__
        'wrapper_do_twice'
        
        >>> help(say_whee)
        Help on function wrapper_do_twice in module decorators:
        
        wrapper_do_twice()
        ```
        
        However, after being decorated, **say\_whee()** has gotten very confused abt its identity. It now reports being the **wrapper\_do\_twice()** inner function inside the **do\_twice()** decorator. Although technically true, it is not useful information.
        
        to fix this, decorators should use the @functools.wraps decorator, which will preserve information about the original function. Update [decorators.py](http://decorators.py) again:
        
        ```python
        import functools
        
        def do_twice(func):
        	@functools.wraps(func)
        	def wrapper_do_twice(*args, **kwargs):
        		func(*args, **kwargs)
        		return func(*args, **kwargs)
        	return wrapper_do_twice
        ```
        
        there is nothing that needs to be changed abt the decorated say\_whee() function:
        
        ```python
        >>> say_whee
        <function say_whee at 0x7ff79a60f2f0>
        
        >>> say_whee.__name__
        'say_whee'
        
        >>> help(say_whee)
        Help on function say_whee in module whee:
        
        say_whee()
        ```
        
        much better! now say\_whee() is still itself after decoration.
        
        note: the @functools.wraps decorator uses the function functools.update\_wrapper(0 to update special attributes like **name** and **doc** that are used in the introspection.
        
-   a few real-world examples
    
    let's look at a few more useful examples of decorators. They will mainly follow the same pattern.
    
    ```python
    import functools
    
    def decorator(func):
    	@functools.wraps(func)
    	def wrapper_decorator(*args, **kwargs)
    		# do something before
    		value = func(*args, **kwargs)
    		# do something after
    		return value
    	return wrapper_decorator
    ```
    
    this formula is a good boilerplate template for building more complex decorators.
    
    -   timing functions
        
        start by creating a @timer decorator. It will measure the time a function takes to execute and print the duration to the console.
        
        here's the code:
        
        ```python
        import functools
        import time
        
        def timer(func):
        	"""Print the runtime of the decorated function"""
        	@functools.wraps(func)
        	def wrapper_timer(*args, **kwargs):
        		start_time = time.perf_counter() # 1
        		value = func(*args, **kwargs)
        		end_time = time.perf_counter() # 2
        		run_time = end_time - start_time # 3
        		print(f"Finished {func.__name__!r} in {run_time:.4f} secs")
        		return value
        	return wrapper_timer
        
        @timer
        def waste_some_time(num_times):
        	for _ in range(num_times):
        		sum([i**2 for i in range(10000)])
        ```
        
        this decorator works by storing the time just before the function starts running(at the line marked #1) and just after the function finishes(at #2). The time the function takes is then the difference between the two(at #3). The **time.perf\_counter()** function is used , which does a good job of measuring time intervals. Here are some examples of timings:
        
        ```python
        >>> waste_some_time(1)
        Finished 'waste_some_time' in 0.0010 secs
        
        >>> waste_some_time(999)
        Finished 'waste_some_time' in 0.3260 secs
        ```
        
        note: the @timer decorator is great if you just want to get an idea abt the runtime of your functions. If you want to do more precise measurements of code, you should instead consider the timeit module in the standard library. it temporarily disables garbage collection and runs multiple trials to strip out noise from quick function calls.
        
    -   debugging code
        
        the following @debug decorator will print the arguments a function is called with as well as its return value every time the function is called:
        
        ```python
        import functools
        
        def debug(func):
        	"""Print the function signature and return value"""
        	def wrapper_debug(*args, **kwargs):
        		args_repr = [repr(a) for a in args] # 1
        		kwargs_repr = [f"{k}={v!r}" for k, v in kwargs.items()] # 2
        		signature = ", ".join(args_repr + kwargs_repr) # 3
        		print(f"Calling {func.__name__}({signature})")
        		value = func(*args, **kwargs)
        		print(f"{func.__name__!r} returned {value!r}") # 4
        		return value
        	return wrapper_debug
        ```
        
        the signature is created by joining the **string representations** of all the arguments. The numbers in the following list correspond to the numbered comments in the code:
        
        1.  Create a list of the positional arguments. Use repr() to get a nice string representing each argument.
        2.  Create a list of the keyword arguments. The f-string formats each argument as key=value while the !r specifier means that repr() is used to represent the value.
        3.  the lists of positional and keyword arguments is joined together to one signature string w/ each argument separated by a comma.
        4.  the return value is printed after the function is executed.
        
        let's see how the decorator works in practice by applying it to a simple function w/ one position and one keyword argument:
        
        ```python
        @debug
        def make_greeting(name, age=None):
        	if age is None:
        		return f"Howdy {name}!"
        	else:
        		return f"Whoa {name}! {age} already, you are growing up!"
        ```
        
        note how the @debug decorator prints the signature and return value of the **make\_greeting()** function:
        
        ```python
        >>> make_greeting("Benjamin")
        Calling make_greeting('Benjamin')
        'make_greeting' returned 'Howdy Benjamin!'
        'Howdy Benjamin!'
        
        >>> make_greeting("Richard", age=112)
        Calling make_greeting('Richard', age=112)
        'make_greeting' returned 'Whoa Richard! 112 already, you are growing up!'
        'Whoa Richard! 112 already, yoou are growing up!'
        
        >>> make_greeting(name = "Dorrisile", age=116)
        Calling make_greeting(name='Dorrisile', age=116)
        'make_greeting' returned 'Whoa Dorrisile! 116 already, you are growing up!'
        'Whoa Dorrisile! 116 already, you are growing up!'
        ```
        
        the example might not seem immediately useful since the @debug decorator just repeats what is written. It's more powerful when applied to small convenience functions that isn't directly called by yourself.
        
        the following example calculates an approximation to the mathematical constant _e_:
        
        ```python
        import math
        from decorators import debug
        
        #Apply a decorator to a standard library function
        math.factorial = debug(math.factorial)
        
        def approximate_e(terms=18):
        	return sum(1 / math.factorial(n) for n in range(terms))
        ```
        
        this examples also shows how you can apply a decorator to a function that has already been defined. The approximation of _e_ is based on the following series expansion:
        
        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4188d3f6-5084-4932-a77f-fac307177872/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4188d3f6-5084-4932-a77f-fac307177872/Untitled.png)
        
        when calling the **approximate\_e()** function, you can see the @debug decorator at work:
        
        ```python
        >>> approximate_e(5)
        Calling factorial(0)
        'factorial' returned 1
        Calling factorial(1)
        'factorial' returned 1
        Calling factorial(2)
        'factorial' returned 2
        Calling factorial(3)
        'factorial' returned 6
        Calling factorial(4)
        'factorial' returned 24
        2.708333333333333
        ```
        
        in this example, there is a decent approximation to the true value _e_ = 2.718281828, adding only 5 terms.
        
    -   slowing down code
        
        the most common use case is that you want to rate-limit a function that continuously checks whether a resource— like a web page— has changed. The @slow\_down decorator will sleep one second before it calls the decorated function:
        
        ```python
        import functools
        import time
        
        def slow_down(func):
        	"""Sleep 1 second before calling the function"""
        	@functools.wraps(func)
        	def wrapper_slow_down(*args, **kwargs):
        		time.sleep(1)
        		return func(*args, **kwargs)
        	return wrapper_slow_down
        
        @slow_down
        def countdown(from_number):
        	if from_number < 1:
        		print("Liftoff!")
        	else:
        		print(from_number)
        		countdown(from_number - 1)
        ```
        
        effect of the @slow\_down decorator(will be seen when run code urself):
        
        ```python
        >>> countdown(3)
        3
        2
        1
        Liftoff!
        ```
        
        note: the countdown() function is a recursive function.
        
        the @slow\_down decorator always sleeps for one second.
        
    -   registering plugins
        
        decorators don't have to wrap the function they're decorating. They can also simply register that a function exists and return it unwrapped. This can be used, for instance, to create a light-weight plug-in architecture:
        
        ```python
        import random
        PLUGINS = dict()
        
        def register(func):
        	"""Register a function as a plug-in"""
        	PLUGINS[func.__name__] = func
        	return func
        
        @register
        def say_hello(name):
        	return f"Hello {name}"
        
        @register
        def be_awesome(name):
        	return f"Yo {name}, together we are the awesomest!"
        
        def randomly_greet(name):
        	greeter, greeter_func = random.choice(list(PLUGINS.items()))
        	print(f"Using {greeter!r}")
        	return greeter_func(name)
        
        ```
        
        The @register decorator simply stores a reference to the decorated function in the global PLUGINS dict. Note that writing an inner function or using @functools.wraps is not necessary in this example bc u are returning the original function unmodified.
        
        the randomly\_greet() function randomly chooses one of the registered functions to use. Note that the PLUGINS dictionary already contains references to each function object that's registered as a plugin:
        
        ```python
        >>> PLUGINS
        {'say_hello': <function say_hello at 0x7f768eae6730>, 'be_awesome': <function be_awesome at 0x7f768eae67b8>}
        
        >>> randomly_greet("Alice")
        Using 'say_hello'
        'Hello Alice'
        ```
        
        the main benefit of this simple plugin architecture is that you don't need to maintain a list of which plugins exist. That list is created when the plugins register themselves. This makes it trivial to add a new plugin: just define the function and decorate it w/ @register.
        
        globals() in Python has some similarities to how the plugin architecture works. globals() gives access to all global variables in the current scope, including the plugins:
        
        ```python
        >>> globals()
        {..., # Lots of variables not shown here.
        	'say_hello': <function say_hello at 0x7f768eae6730>,
        	'be_awesome': <function be_awesome at 0x7f768eae67b8>,
        	'randomly_greet': <function randomly_greet at 0x7f768eae6840>}
        ```
        
        using the @register decorator, you can create your own curated list of interesting variables, effectively hand-picking some functions from globals().
        
    -   is the user logged in code
        
        final simple decorator example is commonly used when working w/ web framework. In this example, using Flask to set up a /secret webpage that should only be visible to users that are logged in or otherwise authenticated:
        
        ```python
        from flask import Flask, g, request, redirect, url_for import functools
        app = Flask(__name__)
        
        def login_required(func):
        	"""Make sure user is logged in before proceeding"""
        	@functools.wraps(func)
        	def wrapper_login_required(*args, **kwargs):
        		if g.user is None:
        			return redirect(url_for("login", next=request.url))
        		return func(*args, **kwargs)
        	return wrapper_login_required
        
        @app.route("/secret")
        @login_required
        def secret():
        	...
        ```
        
        while this gives an idea abt how to add authentication to a web framework, should usually not write these types of decorators yourself. For Flask, the Flask-Login extension can be used instead, which adds more security and functionality
        
-   fancy decorators
    
    -   decorating classes
        
        there are 2 different ways you can use decorators on classes. The first is very close to the way w/ functions: you can decorate the methods of a class.
        
        Some commonly used decorators that are even built-ins in Python are @classmethod, @staticmethod, and @property. The @classmethod and @staticmethod decorators are used to define methods inside a class namespace that are not connected to a particular instance of that class. The @property decorator is used to customize getters and setters for class attributes.
        
        -   example using built-in class decorators
            
            the following definition of a Circle class uses @classmethod, @staticmethod, and @property decorators:
            
            ```python
            class Circle:
            	def __init__(self, radius):
            		self._radius = radius
            	
            	@property
            	def radius(self):
            		"""Get value of radius"""
            		return self._radius
            
            	@radius.setter
            	def radius(self, value):
            		"""Set radius, raise error if negative"""
            		if value >= 0:
            			self._radius = value
            		else:
            			raise ValueError("Radius must be positive")
            
            	@property
            	def area(self):
            		"""Calculate area inside circle"""
            		return self.pi() * self.radius**2
            
            	def cylinder_volume(self, height):
            		"""Calculate volume of cylinder with circle as base"""
            		return self.area * height
            
            	@classmethod
            	def unit_circle(cls):
            		"""Factory method creating a circle with radius 1"""
            		return cls(1)
            
            	@staticmethod
            	def pi():
            		"""Value of π, could use math.pi instead though"""
            		return 3.1415926535
            ```
            
            in this class,
            
            -   .cylinder\_volume() is a regular method
            -   .radius is a mutable property: it can be set to a different value. However, by defining a setter method, we can do some error testing to make sure it's not set to a nonsensical negative number. Properties are accessed as attributes without parentheses
            -   .area is an immutable property: properties without .setter() methods can't be changed. Even though it is defined as a method, it can be retrieved as an attribute without parentheses.
            -   .unit\_circle() is a class method. It's not bound to one particular instance of Circle. Class methods are often used as factory methods that can create specific instances of the class
            -   .pi() is a static method. It's not really dependent on the Circle class, except that it is part of its namespace. Static methods can be called on either an instance or the class.
            
            the class can(for example) be used like this:
            
            ```python
            >>> c = Circle(5)
            >>> c.radius
            5
            
            >>> c.area
            78.5398163375
            
            >>> c.radius = 2
            >>> c.area
            12.566370614
            
            >>> c.area = 100
            AttributeError: can't set attribute
            
            >>> c.cylinder_volume(height=4)
            50.265482456
            
            >>> c.radius = -1
            ValueError: Radius must be positive
            
            >>> c = Circle.unit_circle()
            >>> c.radius
            1
            
            >>> c.pi()
            3.1415926535
            
            >>> Circle.pi()
            3.1415926535
            ```
            
        
        let's define a class where we decorate some of its methods using the @debug and @timer decorators from earlier(assuming they are in the decorators file):
        
        ```python
        from decorators import debug, timer
        
        class TimeWaster:
        	@debug
        	def __init__(self, max_num):
        		self.max_num = max_num
        
        	@timer
        	def waste_time(self, num_times):
        		for _ in range(num_times):
        			sum([i**2 for i in range(self.max_num)])
        ```
        
        using the class, you can see the effect of the decorators:
        
        ```python
        >>> tw = TimeWaster(1000)
        Calling __init__(<time_waster.TimeWaster object at 0x7efccce03908>, 1000)
        '__init__' returned None
        
        >>> tw.waste_time(999)
        Finished 'waste_time' in 0.3376 secs
        ```
        
        the other way to use decorators on classes is to **decorate the whole class**. This is(for example) done in the new dataclasses module in Python 3.7:
        
        ```python
        from dataclasses import dataclass
        
        @dataclass
        class PlayingCard:
        	rank: str
        	suit: str
        ```
        
        the meaning of the syntax is similar to the function decorators. In the example above, you could have done the decoration by writing PlayingCard = dataclass(PlayingCard).
        
        A common use of class decorators is to be a simpler alternative to some use-cases of metaclasses. In both classes, you care changing the definition of a class dynamically.
        
        Writing a class decorator is very similar to writing a function decorator. The only difference is that the decorator will receive a class and not a function as an argument. In fact, all the decorators already mentioned will work as class decorators. When you are using them on a class instead of a function, their effect might not be what is wanted. In the following example, the @timer decorator is applied to a class:
        
        ```python
        from decorators import timer
        
        @timer
        class TimeWaster:
        	def __init__(self, max_num):
        		self.max_num = max_num
        
        	def waste_time(self, num_times):
        		for _ in range(num_times):
        			sum([i**2 for i in range(self.max_num)])
        ```
        
        decorating a class doesn't decorate its methods. Recall that @timer is just shorthand for TimeWaster = timer(TimeWaster).
        
        Here, @timer only measures the time it takes to instantiate the class:
        
        ```python
        >>> tw = TimeWaster(1000)
        Finished 'TimeWaster' in 0.0000 secs
        
        >>> tw.waste_time(999)
        >>>
        ```
        
        later an example will be seen defining a proper class decorator, namely @singleton, which ensures that there is only one instance of a class.
        
    -   nesting decorators
        
        you can apply several decorators to a function by stacking them on top of each other:
        
        ```python
        from decorators import debug, do_twice
        
        @debug
        @do_twice
        def greet(name):
        	print(f"Hello {name}")
        ```
        
        think abt this as the decorators being executed in the order they are listed. In other words, @debug calls @do\_twice, which calls greet(), or debug(do\_twice(greet())):
        
        ```python
        >>> greet("Eva")
        Calling greet('Eva')
        Hello Eva
        Hello Eva
        'greet' returned None
        ```
        
        observe the difference if we change the order of @debug and @do\_twice:
        
        ```python
        from decorators import debug, do_twice
        
        @do_twice
        @debug
        def greet(name):
        	print(f"Hello {name}")
        ```
        
        in this case, @do\_twice will be applied to @debug as well:
        
        ```python
        >>> greet("Eva")
        Calling greet('Eva')
        Hello Eva
        'greet' returned None
        Calling greet('Eva')
        Hello Eva
        'greet' returned None
        ```
        
    -   decorators with arguments
        
        sometimes, it's useful to **pass arguments to the decorators**. For instance, @do\_twice could be extended to a @repeat(num\_times) decorator. The number of times to execute the decorated function could then be given as an argument.
        
        This would allow something like this to be done:
        
        ```python
        @repeat(num_times=4)
        def greet(name):
        	print(f"Hello {name}")
        ```
        
        ```python
        >>> greet("World")
        Hello World
        Hello World
        Hello World
        Hello World
        ```
        
        so far, the name written after the @ has referred to a function object that can be called with another function. To be consistent, you then need repeat(num\_times=4) to return a function object that can act as a decorator. In general, you want something like the following:
        
        ```python
        def repeat(num_times):
        	def decorator_repeat(func):
        		... #create and return a wrapper function
        	return decorator_repeat
        ```
        
        typically, the decorator creates and returns an inner wrapper function, so writing the example out in full will give you an inner function within an inner function:
        
        ```python
        def repeat(num_times):
        	def decorator_repeat(func):
        		@functools.wraps(func)
        		def wrapper_repeat(*args, **kwargs):
        			for _ in range(num_times):
        				value = func(*args, **kwargs)
        			return value
        		return wrapper_repeat
        	return decorator_repeat
        ```
        
        starting with the innermost function,
        
        ```python
        def wrapper_repeat(*args, **kwargs):
        	for _ in range(num_times):
        		value = func(*args, **kwargs)
        	return value
        ```
        
        this wrapper\_repeat() function takes arbitrary arguments and returns the value of the decorated function, func(). This wrapper function also contains the loop that calls the decorated function num\_times times. This is no different from the other wrapper functions that have been seen, except that it is using the num\_times parameter that must be supplied from the outside.
        
        One step out, there will be the decorator function:
        
        ```python
        def decorator_repeat(func):
        	@functools.wraps(func)
        	def wrapper_repeat(*args, **kwargs):
        		...
        	return wrapper_repeat
        ```
        
        again, decorator\_repeat() looks exactly like any other decorator function, except that it's named differently. That's because the base name repeat() is reserved for the outermost function, which is the one the user will call.
        
        as already seen, the outermost function returns a reference to the decorator function:
        
        ```python
        def repeat(num_times);
        	def decorator_repeat(func);
        		...
        	return decorator_repeat
        ```
        
        there are a few subtle things happening in the repeat() function:
        
        -   defining decorator\_repeat() as an inner function means that repeat() will refer to a function object— decorator\_repeat. Earlier, the repeat was used without parentheses to refer to the function object. The added parentheses are necessary when defining decorators that take arguments.
        -   the num\_times argument is seemingly not used in repeat() itself. But by passing num\_times a closure is created where the value of num\_times is stored until it will be used later by wrapper\_repeat().
        
        ```python
        @repeat(num_times=4)
        def greet(name):
        	print(f"Hello {name}")
        ```
        
        ```python
        >>> greet("World")
        Hello World
        Hello World
        Hello World
        Hello World
        ```
        
        this yields the expected result.
        
    -   decorators w/ and w/o arguments
        
        can also define decorators that can be used both with and without arguments. This most likely won't be needed, but flexibility is a good thing to have.
        
        When a decorator uses arguments. you need to add an extra outer function. The challenge is for the code to figure out if the decorator has been called with or without arguments.
        
        Since the function to decorate is only passed in directly if the decorator is called without arguments, the function must be an optional argument. This means that the decorator arguments must all be specified by keyword. This can be enforced with the special \* syntax, which means that all following parameters are keyword-only:
        
        ```python
        def name(_func=None, *, kw1=val1, kw2=val2, ...): # 1
        	def decorator_name(func):
        		... # create and return a wrapper function
        	if _func is None:
        		return decorator_name # 2
        	else:
        		return decorator_name(_func) # 3
        ```
        
        here, the \_func argument acts as a marker, noting whether the decorator has been called with arguments or not:
        
        1.  if name has been called without arguments, the decorated function will be passed in as \_func. If it has been called w/ arguments, then \_func will be None, and some of the keyword arguments may have been changed from their default values. The \* in the argument list means that the remaining arguments can't be called as positional arguments.
        2.  in this case, the decorator was called with arguments. Return a decorator function that can read and return a function.
        3.  In this case, the decorator was called without arguments. Apply the decorator to the function immediately.
        
        using this boilerplate on the @repeat decorator in the previous section, the following can be written:
        
        ```python
        def repeat(_func=None, *, num_times=2):
        	def decorator_repeat(func):
        		@functools.wraps(func)
        		def wrapper_repeat(*args, **kwargs);
        			for _ in range(num_times):
        				value = func(*args, **kwargs)
        			return value
        		return wrapper_repeat
        	
        	if _func is None:
        		return decorator_repeat
        	else:
        		return decorator_repeat(_func)
        ```
        
        compare this with the original @repeat. The only changes are the added \_func parameter and the if-else at the end.
        
        there is an alternative solution using functools.partial().
        
        these examples show that @repeat can now be used with or without arguments:
        
        ```python
        @repeat
        def say_whee():
        	print("Whee!")
        
        @repeat(num_times=3)
        def greet(name):
        	print(f"Hello {name}")
        ```
        
        recall that the default value of num\_times is 2:
        
        ```python
        >>> say_whee()
        Whee!
        Whee!
        
        >>> greet("Penny")
        Hello Penny
        Hello Penny
        Hello Penny
        ```
        
    -   stateful decorators
        
        sometimes it's useful to have a decorator that can keep track of state. As a simple example, a decorator will be created that counts the number of times a function is called.
        
        note: pure functions return a value based on given arguments. Stateful decorators are quite the opposite, where the return value will depend on the current state, as well as the given arguments.
        
        In simple cases, you can use function attributes:
        
        ```python
        import functools
        
        def count_calls(func):
        	@functools.wraps(func)
        	def wrapper_count_calls(*args, **kwargs):
        		wrapper_count_calls.num_calls += 1
        		print(f"Call {wrapper_count_calls.num_calls} of {func.__name__!r}")
        		return func(*args, **kwargs)
        	wrapper_count_calls.num_calls = 0
        	return wrapper_count_calls
        
        @count_calls
        def say_whee():
        	print("Whee!")
        ```
        
        the state, or number of calls to the function, is stored in the function attribute .num\_calls on the wrapper function. Here is the effect of using it:
        
        ```python
        >>> say_whee()
        Call 1 of 'say_whee'
        Whee!
        
        >>> say_whee()
        Call 2 of 'say_whee'
        Whee!
        
        >>> say_whee.num_calls
        2
        ```
        
    -   classes as decorators
        
        the typical way to maintain state is by using classes. You can rewrite the @count\_calls example from the previous section **using a class as a decorator**.
        
        recall that the decorator syntax @my\_decorator is just an easier way of saying func = my\_decorator(func). Therefore, if my\_decorator is a class, it needs to take func as an argument in its **init**() method. Furthermore, the class instance needs to be callable so that it can stand in for the decorated function.
        
        for a class instance to be callable, you implement the special .**call**() method:
        
        ```python
        class Counter:
        	def __init__(self, start=0):
        		self.count = start
        
        	def __call__(self):
        		self.count += 1
        		print(f"Current count is {self.count}")
        ```
        
        the .**call**() method is executed every time you try to call an instance of the class:
        
        ```python
        >>> counter = Counter()
        >>> counter()
        Current count is 1
        
        >>> counter()
        Current count is 2
        
        >>> counter.count
        2
        ```
        
        therefore, a typical implementation of a decorator class needs to implement .**init**() and .**call**():
        
        ```python
        import functools
        
        class CountCalls:
        	def __init__(self, func);
        		functools.update_wrapper(self, func)
        		self.func = func
        		self.num_calls = 0
        
        	def __call__(self, *args, **kwargs):
        		self.num_calls += 1
        		print(f"Call {self.num_calls} of {self.func.__name__!r}")
        		return self.func(*args, **kwargs)
        
        @CountCalls
        def say_whee():
        	print("Whee!")
        ```
        
        the .**init**() method must store a reference to the function and can do any other necessary initialization. The .**call**() method will be called instead of the decorated function. It does essentially the same thing as the wrapper() function in the earlier examples. Note that the functools.update\_wrapper() function has to be used instead of @functools.wraps.
        
        This @CountCalls decorator works the same as the one in the previous section:
        
        ```python
        >>> say_whee()
        Call 1 of 'say_whee'
        Whee!
        
        >>> say_whee()
        Call 2 of 'say_whee'
        Whee!
        
        >>> say_whee.num_calls
        2
        ```
        

[more here](https://realpython.com/primer-on-python-decorators/#more-real-world-examples)