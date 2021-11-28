these provide a way to match only one of a specific set of characters.

a character class is created by putting the characters it matches inside **square brackets**.

```python
import re

pattern = r"[aeiou]"

if re.search(pattern, "grey"):
	print("Match 1")

if re.search(pattern, "qwertyuiop"):
	print("Match 2")

if re.search(pattern, "rhythm myths"):
	print("Match 3")
```

note: the pattern **\[aeiou\]** in the **search** function matches all strings that contain any one of the characters defined.

```
i.e. [abc][def] would match any letter out of "abc", then any out of "def"
```

character classes can also match ranges of characters.

i.e.

the class **\[a-z\]** matches any lowercase alphabetic character

the class **\[G-P\]** matches any uppercase character from G to P

the class **\[0-9\]** matches any digit.

Multiple ranges can be included in one class. For example, **\[A-Za-z\]** matches a letter of any case.

```python
import re

pattern = r"[A-Z][A-Z][0-9]"

if re.search(pattern, "LS8"):
	print("Match 1")

if re.search(pattern, "E3"):
	print("Match 2")

if re.search(pattern, "1ab"):
	print("Match 3")

#this pattern matches strings that contain two alphabetic uppercase letters followed by a digit.
```

placing a **^** at the start of a character class **inverts** it.

This causes it to match any character other than the ones included.

Other metacharacters such as **$** and **.** have no meaning within character classes.

In addition, the metacharacter **^** has no meaning unless it's the first character in the class.

```python
import re

pattern = r"[^A-Z]"

if re.search(pattern, "this is all quiet"):
	print("Match 1")

if re.search(pattern, "AbCdEfG123"):
	print("Match 2")

if re.search(pattern, "THISISALLSHOUTING"):
	print("Match 3")

#the pattern [^A-Z] excludes uppercase strings. Note that the ^ should be inside the brackets to invert the character class.
```