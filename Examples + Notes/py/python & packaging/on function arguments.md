-   \*args
    
    Python allows to have functions with **varying numbers of arguments**.
    
    Using \***args** as a function parameter enables the user to pass an arbitrary number of arguments to that function. The arguments are then accessible as the tuple **args** in the body of the function.
    
    ```python
    def function(named_arg, *args):
    	print(named_arg)
    	print(args)
    
    function(1, 2, 3, 4, 5)
    ```
    
    note: the parameter \*args must come after the named parameters to a function. The name args is just a convention; can choose to use another.
    
-   default values
    
    named parameters to a function can be made optional by giving them a default value.
    
    These must come after named parameters without a default value.
    
    ```python
    def function(x, y, food="spam"):
    	print(food)
    
    function(1, 2)
    function(3, 4, "egg")
    ```
    
    in case the argument is passed in, the default value is ignored. If the argument is not passed in, the default value is used.
    
-   \*\*kwargs
    
    standing for keyword arguments.
    
    This allows the user to handle named arguments that have not been defined in advance.
    
    The keyword arguments return a dictionary in which the keys are the argument names, and the values are the argument values.
    
    ```python
    def my_func(x, y=7, *args, **kwargs):
    	print(kwargs)
    
    my_func(2, 3, 4, 5, 6, a=7, b=8)
    ```
    
    and b are the names of the arguments that were passed to the function call.
    
    note: the arguments returned by \*\*kwargs aren't included in \*args.