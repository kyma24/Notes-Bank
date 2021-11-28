-   basics
    
    a group can be created by surrounding part of a regular expression with **parentheses**.
    
    this means that a group can be given as an argument to metacharacters such as \* and ?.
    
    ```python
    #i.e.
    import re
    
    pattern = r"egg(spam)*"
    
    if re.match(pattern, "egg"):
    	print("Match 1")
    
    if re.match(pattern, "eggspamspamspamegg"):
    	print("Match 2")
    
    if re.match(pattern, "spam"):
    	print("Match 3")
    
    #note: (spam) represents a group in the example above
    #i.e. '([^aeiou][aeiou][^aeiou])+' would match one or more repetitions of a non-vowel, a vowel and a non-vowel.
    ```
    
-   content
    
    the content of groups in a match can be accessed using the **group** function.
    
    A call of **group(0)** or **group()** returns the whole match.
    
    A call of **group(n)**, where **n** is greater than 0, returns the **n**th group from the left.
    
    The method **groups()** returns all groups up from 1.
    
    ```python
    import re
    
    pattern = r"a(bc)(de)(f(g)h)i"
    
    match = re.match(pattern, "abcdefghijklmnop")
    if match:
    	print(match.group())
    	print(match.group(0))
    	print(match.group(1))
    	print(match.group(2))
    	print(match.groups())
    
    #note: as seen, groups can be nested.
    #i.e. group(3) of a match of 1(23)(4(56)78)9(0) would be 56.
    ```
    
-   types
    
    several kinds of special groups.
    
    two useful ones are **named groups** and **non-capturing groups**.
    
    **Named groups** have the format **(?P<name>...)**, where **name** is the name of the group, and ... is the content. They behave exactly the same as normal groups, except they can be accessed by **group(name)** in addition to its number.
    
    **Non-capturing groups** have the format **(?:...)**. They aren't accessible by the group method, so they can be added to an existing regular expression without breaking the numbering.
	
```python
#i.e.
import re

pattern = r"(?P<first>abc)(?:def)(ghi)"

match = re.match(pattern, "abcdefghi")
if match:
	print(match.group("first"))
	print(match.groups())

#the result of len(match.groups()) of a match of (a)(b(?:c)(d)(?:e)) will be Group 1 - (a) Group 2 - (bd) Group 3 - (d) Length of Groups = 3
```
    
-   metacharacters(|)
    
    Another important metacharacter is **|**.
    
    This means "or", so **red|blue** matches either "red" or "blue".
    
    ```python
    #i.e.
    import re
    
    pattern = r"gr(a|e)y"
    
    match = re.match(pattern, "gray")
    if match:
    	print("Match 1")
    
    match = re.match(pattern, "grey")
    if match:
    	print("Match 2")
    
    match = re.match(pattern, "griy")
    if match:
    	print("Match 3")
    ```