The built-in functions map and filter are very useful higher-order functions that operate on lists(or similar objects called **iterables**).

-   map
    
    The function **map** takes a function and an iterable as its arguments, and returns a new iterable with the function applied to each argument.
    
    ```python
    def add_five(x):
    	return x + 5
    
    nums = [11, 22, 33, 44, 55]
    result = list(map(add_five, nums))
    print(result)
    ```
    
    this same result could be more easily reached by using the lambda syntax.
    
    ```python
    nums = [11, 22, 33, 44, 55]
    
    result = list(map(lambda x: x+5, nums))
    print(result)
    ```
    
    to convert the result into a list, we used list explicitly.
    
-   filter
    
    the function **filter** filters an iterable by removing items that don't match a predicate(a function that returns a boolean)
    
    ```python
    #i.e.
    nums = [11, 22, 33, 44, 55]
    res = list(filter(lambda x: x%2==0, nums))
    print(res)
    ```
    
    like **map**, the result has to be explicitly converted to a list if you want to print it.