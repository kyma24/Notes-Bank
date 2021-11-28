-   basics
    
    these are what make regular expressions more powerful than normal string methods.
    
    they allow you to create regular expressions to represent concepts like "one or more repetitions of a vowel".
    
    the existence of metacharacters poses a problem if want to create a regular expression(or **regex**) that matches a literal metacharacter, such as "$". This can be done by escaping the metacharacters by putting a **backslash** in front of them.
    
    however, this can also cause problems, since backslashes also have an escaping function in normal Python strings. This can mean putting three or four backslashes in a row to do all the escaping.
    
    note: to avoid this, can use a raw string, which is a normal string with an "r" in front of it.
    
-   metacharacters(.)
    
    one metacharacter is .(dot).
    
    this matches **any character**, other than a new line.
    
    ```python
    import re
    
    pattern = r"gr.y"
    
    if re.match(pattern, "grey"):
    	print("Match 1")
    
    if re.match(pattern, "gray"):
    	print("Match 2")
    
    if re.match(pattern, "blue"):
    	print("Match 3")
    
    #will only print 'Match 1' and 'Match 2' because the third statement does not follow the pattern.
    ```
    
    note: '....' matches any four character string with no newlines.
    
-   more simple metacharacters(^ and $)
    
    The next two metacharacters are **^** and **$**.
    
    These match the **start** and **end** of a string, respectively.
    
    ```python
    import re
    
    pattern = r"^gr.y$"
    
    if re.match(pattern, "grey"):
    	print("Match 1")
    
    if re.match(pattern, "gray"):
    	print("Match 2")
    
    if re.match(pattern, "stingray"):
    	print("Match 3")
    ```
    
    note: the pattern "**^gr.y$**" means that the string should start with gr, then follow with any character except a newline, and end with a y.
    
-   more(\*, +, ?, {, })
    
    some more metacharacters are \*\*\* + ? {\*\* and **}**.
    
    -   These specify numbers of repetitions.
        
        The metacharacter \*\*\*\*\* means "zero or more repetitions of the previous thing". It tries to match as many repetitions as possible. The "previous thing" can be a single character, a class, or a group of characters in parentheses.
        
        ```python
        import re
        
        pattern = r"egg(spam)*"
        
        if re.match(pattern, "egg"):
        	print("Match 1")
        
        if re.match(pattern, "eggspamspamegg"):
        	print("Match 2")
        
        if re.match(pattern, "spam"):
        	print("Match 3")
        ```
        
        this example matches strings that start w/ "egg" and follow with zero or more "spam"s. Tus, \[a^\]\* will match zero or more repetitions of "a" or "^"
        
    -   very similar to \*, except it means "**one** or more repetitions" as opposed to "zero or more repetitions."
        
        ```python
        import re
        
        pattern = r"g+"
        
        if re.match(pattern, "g"):
        	print("Match 1")
        
        if re.match(pattern, "gggggggggggggg"):
        	print("Match 2")
        
        if re.match(pattern, "abc"):
        	print("Match 3")
        ```
        
        summarize:
        
        -   -   matches 0 or more occurrences of the preceding expression
        -   -   matches 1 or more occurrences of the preceding expression.
    -   ?
        
        means "zero or one repetitions".
        
        ```python
        import re
        
        pattern = r"ice(-)?cream"
        
        if re.match(pattern, "ice-cream"):
        	print("Match 1")
        
        if re.match(pattern, "icecream"):
        	print("Match 2")
        
        if re.match(pattern, "sausages"):
        	print("Match 3")
        
        if re.match(pattern, "ice--ice"):
        	print("Match 4")
        ```
        
    -   {}
        
        curly braces can be used to represent the number of repetitions between two numbers.
        
        the regex {x,y} means "between x and y repetitions of something".
        
        Hence {0,1} is the same thing as ?.
        
        if the first number is missing, it is taken to be zero. If the second number is missing, it is taken to be infinity.
        
        ```python
        import re
        
        pattern = r"9{1,3}$"
        
        if re.match(pattern, "9"):
        	print("Match 1")
        
        if re.match(pattern, "999"):
        	print("Match 2")
        
        if re.match(pattern, "9999"):
        	print("Match 3")
        
        #note: "9{1,3}$" matches string that have 1 to 3 nines.
        ```