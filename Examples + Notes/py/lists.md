```py
>>>fruit = 'banana'
>>>pos = fruit.find('na')
#.find finds first occurance of substring
>>>print pos
2
>>>aa = fruit.find('z')
>>>print aa
-1
# ^ if substring is not found, returns this
```

```py
>>>greet = 'Hello Bob'
>>>nstr = greet.replace('Bob','Jane')
>>>print nstr
Hello Jane
>>>greet = 'Hello Bob'
>>>nstr = greet.replace('o','X')
>>>print nstr
HellX BXb
>>>
#replace() function replaces ALL occurences of the search string with the replacement string
```

```py
>>>greet = ' Hello Bob '
>>>greet.lstrip()
'Hello Bob '
>>>greet.rstrip()
' Hello Bob'
>>>greet.strip()
'Hello Bob'
```

```py
>>>line = 'Please have a nice day'
>>>line.startswith('Please')
True
>>>line.startswith('p')
False
>>>line.startswith('P')
True
```

```py
>>>data = 'From kimberley.y.ma@gmail.com Sat December 12 03:13:24 2020
>>>atpos = data.find('@')
>>>print(atpos)

>>>sppos = data.find(' ',atpos)
>>>print(sspos)

>>>host = data[atpos + 1: sppos]
>>>print host
```

```py
n = [2, 4, 6, 8]
res = 1
for x in n[1:3]:
  res *= x

print(res)

#outputs 24, bc the range doesn't include the 3rd index
```