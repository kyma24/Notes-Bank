to demonstrate a sample usage of regular expressions, create a program to extract addresses from a string

Suppose there is a text that contains an email address:

```python
str = "Please contact info@sololearn.com for assistance"
```

the goal is to extract the substring ["info@sololearn.com](mailto:%22info@sololearn.com)".

A basic email address consists of a word and may include dots or dashes. This is followed by the @ sign and the domain name(the name, a dot, and the domain name suffix).

This is the basis for building the regular expression.

```python
pattern = r"([\\w\\.-]+)@([\\w\\.-]+)(\\.[\\w\\.]+)"
```

**\[\\w\\.-\]+** matches one or more word character, dot or dash.

The regex abv says that the string should contain a word(with dots and dashes allowed), followed by the @ sign, then another similar word, then a dot and another word.

This regex contains three groups:

1.  first part of the email address
2.  domain name without the suffix
3.  the domain suffix

Putting it all together:

```python
import re

pattern = r"([\\w\\.-]+)@([\\w\\.-]+)(\\.[\\w\\.]+)"
str = "Please contact info@sololearn.com for assistance"
m
match = re.search(pattern, str)
if match:
	print(match.group())

#dot character preceded by backslash to treat it as a character
```

in case the string contains multiple email addresses, can use the **re.findall** method instead of **re.search**, to extract all email addresses.

note: a much more complex regex is required to fully validate an email address.