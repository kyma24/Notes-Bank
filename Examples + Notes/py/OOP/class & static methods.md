-   class methods
    
    methods of objects are sometimes called by an instance of a class, which is then passed into the **self** parameter of the method.
    
    **class methods** are different - they are called by a class, which is passed to the **cls** parameter of the method.
    
    a common use of these are factory methods, which instantiate an instance of a class, using different parameters than those usually passed to the class constructor.
    
    class methods are marked with a **classmethod decorator**.
    
    ```python
    class Rectangle:
    	def __init__(self, width, height):
    		self.width = width
    		self.height = height
    
    	def calculate_area(self):
    		return self.width * self.height
    
    	@classmethod
    	def new_square(cls, side_length):
    		return cls(side_length, side_length)
    
    square = Rectangle.new_square(5)
    print(square.calculate_area())
    ```
    
    **new\_square** is a class method & is called on the class, rather than on an instance of the class. It returns a new object of the class **cls**.
    
    note: technically, the parameters **self** and **cls** are just conventions; they could be changed to anything else. However, they are universally followed, so it's wise to stick to using them.
    
-   static methods
    
    static methods are similar to class methods, except they don't receive any additional arguments; they are identical to normal functions that belong to a class
    
    marked w/ **staticmethod** decorator
    
    ```python
    class Pizza:
    	def __init__(self, toppings):
    		self.toppings = toppings
    
    	@staticmethod
    	def validate_topping(topping):
    		if topping == "pineapple"
    			raise ValueError("No pineapples!")
    		else:
    			return True
    
    ingredients = ["cheese", "onions", "spam"]
    if all(Pizza.validate_topping(i) for i in ingredients):
    	pizza = Pizza(ingredients)
    ```
    
    note: static methods behave like plain functions, except for the fact that you can call them from an instance of the class.