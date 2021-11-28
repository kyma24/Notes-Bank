regular expressions in Python can be accessed using the **re** module, which is part of the standard library. After a regular expression is determined, the **re.match** function can be used to determine whether it matches at the **beginning** of a string.

If it does, **match** returns an object representing the match, if not, it returns **None**.

To avoid any confusion while working with regular expressions, raw strings would be used such as **r"expression"**.

Raw strings don't escape anything, which makes use of regular expressions

```python
import re

pattern = r"spam"

if re.match(pattern, "spamspamspam"):
	print("Match")
else:
	print("No match")
```

the above example checks if the pattern "spam" matches the string and prints "Match" if it does.

note: here the pattern is a simple word, but there are various characters, which would have special meaning when they are used in a regular expression.

other functions to match patterns are **re.search** and **re.findall**. The function **re.search** finds the match of a pattern anywhere in the string. The function **re.findall** returns a list of all substrings that match a pattern.

```python
import re

pattern = r"spam"

if re.match(pattern, "eggspamsausagespam"):
	print("Match")
else:
	print("No match")

if re.search(pattern, "eggspamsausagespam"):
	print("Match")
else:
	print("No match")

print(re.findall(pattern, "eggspamsausagespam"))
```

in the example, the match function didn't match the pattern, as it looks at the beginning of the string. The search function found a match in the string.

note: the function **re.finditer** does the same thing as **re.findall**, except it returns an iterator, rather than a list.

the regex search returns an object with several methods that give details about it.

these methods include **group** which returns the string matched, **start** and **end** which return the start and ending positions of the first match, and and **span** which returns the start and end positions of the first match as a tuple.

```python
import re

pattern = r"pam"

match = re.search(pattern, "eggspamsausage")
if match:
	print(match.group())
	print(match.start())
	print(match.end())
	print(match.span())
```