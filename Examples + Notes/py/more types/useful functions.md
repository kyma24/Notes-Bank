-   string functions
    
    python contains many useful built-in functions & methods to accomplish common tasks
    
    **join** - joins a list of strings w/ another string as a separator
    
    **replace** - replaces one substring w/ another string as a separator
    
    **startswith** & **endswith** - determines if there is a substring at the start and end of a string, respectively
    
    To change the case of a string, you can use lower and upper.
    
    the method split is the opposite of join turning a string w/ a certain separator into the list
    
    ```python
    print(", ".join(["spam", "eggs", "ham"]))
    #prints "spam, eggs, ham"
    
    print("Hello ME".replace("ME", "world"))
    #prints "Hello world"
    
    print("This is a sentence.".startswith("This"))
    #prints "True"
    
    print("This is a sentence.".endswith("sentence."))
    #prints "True"
    
    print("This is a sentence.".upper())
    #prints "THIS IS A SENTENCE."
    
    print("AN ALL CAPS SENTENCE".lower())
    #prints "an all caps sentence"
    
    print("spam, eggs, ham".split(", "))
    #prints "['spam', 'eggs', 'ham']"
    ```
    
-   numeric functions
    
    to find the max/min of some numbers or a list, you can use max or min.
    
    to find the distance of a number from 0(abs val), use abs
    
    to round a number to a certain number of decimal places use round
    
    to find the total of a list, use sum
    
    ```python
    print(min(1, 2, 3, 4, 0, 2, 1))
    print(max([1, 4, 9, 2, 5, 6, 8]))
    print(abs(-99))
    print(abs(42))
    print(sum([1, 2, 3, 4, 5]))
    ```
    
-   list functions
    
    often used in conditional statements, all and any take a list as an argument and return True if all or any(respectively) of their arguments evaluate to True(and False otherwise).
    
    The function enumerate can be used to iterate thru the values and indices of the list simultaneously
    
    ```python
    nums = [55, 44, 33, 22, 11]
    
    if all([i > 5 for i in nums]):
    	print("All larger than 5")
    
    if any([i % 2 == 0 for i in nums]):
    	print("At least one is even")
    ```