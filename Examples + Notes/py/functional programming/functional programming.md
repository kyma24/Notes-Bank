-   higher-order functions
    
    this is a style of programming that(as the name suggests) is based around functions.
    
    the key part of functional programming is **higher-order functions**. These functions take other functions as arguments, or return them as results.
    
    ```python
    #i.e.
    def apply_twice(func, arg):
    	return func(func(arg))
    #takes another function as its argument & calls it twice inside its body
    
    def add_five(x):
    	return x + 5
    
    print(apply_twice(add_five, 10))
    ```
    
-   pure functions
    
    functional programming seeks to use **pure functions**. Pure functions have no side effects, and return a value that depends **only** on their arguments. This is how functions in math work: i.e. the cos(x) will, for the same value of x, always return the same result.
    
    ```python
    #i.e. Pure Function
    def pure_function(x, y):
    	temp = x + 2*y
    	return temp / (2*x + y)
    ```
    
    ```python
    #i.e. Impure Function
    some_list = []
    
    def impure(arg):
    	some_list.append(arg)
    #this isn't pure bc it changed the state of some_list
    ```
    
    using pure functions have both advantages and disadvantages.
    
    -   easier to reason abt and test
    -   more efficient. once the function has been evaluated for an input, the result can be stored & referred to the next time the function of that input is needed, reducing the number of times the function is called. This is called memorization
    -   easier to run in parallel
    
    main disadvantage of using only pure functions is that they majorly complicate the otherwise simple task of I/O, since this appears to inherently require side effects.
    
    They can also be more difficult to write in some situations