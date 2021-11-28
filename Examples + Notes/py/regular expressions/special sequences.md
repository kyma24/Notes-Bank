there are various special sequences that can be used in regular expressions. They are written as a backslash followed by another character.

One useful special sequences is a backslash and a number between 1 and 99, e.g. \\1 or \\17. This matches the expression of the group of that number.

```python
#i.e.
import re

pattern = r"(.+) \\1"

match = re.match(pattern, "word word")
if match:
	print("Match 1")

match = re.match(pattern, "?! ?!")
if match:
	print("Match 2")

match = re.match(pattern, "abc cde")
if match:
	print("Match 3")

#note that "(.+) \\1" is not the same as "(.+)(.+)" because \\1 refers to the first group's subexpression, which is the matched expression itself, and not the regex pattern.
#bc of this, (abc|xyz)\\1 would match "abc" or "xyz" followed by the same thing.
```

more useful special sequences are **\\d**, **\\s**, and **\\w**.

These match **digits**, **whitespace**, and **word characters** respectively.

In ASCII mode they are equivalent to \[0-9\], \[\\t\\n\\r\\f\\v\], and \[a-zA-Z0-9\_\].

In Unicode mode they match certain other characters, as well. For instance, **\\w** matchs letters with accents.

Versions of these special sequences with uppercase letters - **\\D**, **\\S**, and **\\W** - mean the opposite to the lowercase versions. For instance, **\\D** matches anything that isn't a digit.

```python
#i.e.
import re

pattern = r"(\\D+\\d)"

match = re.match(pattern, "Hi 999!")
if match:
	print("Match 1")

match = re.match(pattern, "1, 23, 456!")
if match:
	print("Match 2")

match = re.match(pattern, " ! $?")
if match:
	print("Match 3")

#note: (\\D+\\d) matches one or more non-digits followed by a digit.
```

additional special sequences are **\\A**, **\\Z**, and **\\b**.

The sequences **\\A** and **\\Z** match the beginning and end of a string, respectively.

The sequence **\\b** matches the empty string between **\\w** and **\\W** characters, or **\\w** characters and the beginning or end of the string. Informally, it represents the boundary between words.

The sequence **\\B** matches the empty string anywhere else.

```python
#i.e.
import re

pattern = r"\\b(cat)\\b"

match = re.search(pattern, "The cat sat!")
if match:
	print("Match 1")

match = re.search(Pattern, "We s>cat<tered?")
if match:
	print("Match 2")

match = re.search(pattern, "We scattered.")
if match:
	print("Match 3")

#note: \\b(cat\\b basically matches the word "cat" surrounded by word boundaries.
#\\AS...\\b.\\Z would match 'SPAM!' in a search
```