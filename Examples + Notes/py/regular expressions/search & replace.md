one of the most important **re** methods that use regular expressions is **sub**.

```python
re.sub(pattern, repl, string, count=0)
```

this method replaces all occurrences of the **pattern** in string with **repl**, substituting all occurrences, unless **count** provided. this method returns the modified string.

```python
#i.e.
import re

str = "My name is David. Hi David."
pattern = r"David"
newstr = re.sub(pattern, "Sophie", str)
print(newstr)
#replaces all occurrences of David with Sophie
```