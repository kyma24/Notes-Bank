```py
print("""this
is a
multiline
text""")
```

```py
age = 42
print("His age is " + str(age))
```

```py
m = [
    [1, 2, 3],
    [4, 5, 6]
    ]
    
print(m[1][2])
```

```py
number = 3
things = ["string", 0, [1, 2, number], 4.56]
print(things[1])
print(things[2])
print(things[2][2])
#Some types, such as strings, can be indexed like lists.
#Indexing strings behaves as though you are indexing a list
#containing each character in the string.
str = "Hello world!"
print(str[6])
```

```py
name = "AwesomeName"
print  (name[0])
print (name[-1])
#prints A & e
```

```py
#Lists can be multiplied in the same way as you can multiply individual strings,
#and added the same way as well.
nums = [1, 2, 3]
print(nums + [4, 5, 6])
print(nums * 3)
```

```py
#To check if an item is in a list, the in operator can be used.
#It returns True if the item occurs one or more times in the list,
#and False if it doesn't.
words = ["spam", "egg", "spam", "sausage"]
print("spam" in words)
print("egg" in words)
print("tomato" in words)
#The in operator is also used to determine
#whether or not a string is a substring of another string.
```

```py
#To check if an item is not in a list,
#you can use the not operator in one of the following ways:
nums = [1, 2, 3]
print(not 4 in nums)
print(4 not in nums)
print(not 3 in nums)
print(3 not in nums)
```

```py
print (list(range(5)))
#Program returns set [0,1,2,3,4]
```

```py
words = ["Python", "fun"]
index = 1
words.insert(index, "is")
print(words)
#The insert method is similar to append,
#except that it allows you to insert a new item at any position in the list,
#as opposed to just at the end.
#Note: Elements, that are after the inserted item, are shifted to the right.
```

```py
#index method finds the first occurrence of a list item and returns its index.
#If the item isn't in the list, it raises a ValueError.
letters = ['p', 'q', 'r', 's', 'p', 'u']
print(letters.index('r'))
print(letters.index('p'))
print(letters.index('z'))
#There are a few more useful functions and methods for lists:
max(list)# Returns the list item with the maximum value
min(list) #Returns the list item with minimum value
list.count(item) #Returns a count of how many times an item occurs in a list
list.remove(item) #Removes an object from a list
list.reverse() #Reverses items in a list.
#For example, you can count how many 42s are there in the list using:
items.count(42)
#where items is the name of our list.
```

```py
i = 0
while True:
  print(i)
  i = i + 1
  if i >= 5:
    print("Breaking")
    break

print("Finished")
#Break jumps out of loop
```

```py
i = 1
while i<=5:
    print(i)
    i+=1
    if i==3:
      print("Skipping 3")
      continue
#Continue skips current iteration and jumps to next one
```

```py
for v in range(3,9,2):
	print(v)
#This code prints in the following order: 3, 5, 7
# The step value in the range is 2, and the limit is 9.
#The range(a,b,k) function can count backward if k is negative.
#Formula: a, a+k, a+2k
```

```py
#If range is called with one argument,
#it produces an object with values from 0 to that argument.
#If it is called with two arguments,
#it produces values from the first to the second.
#For example:
numbers = list(range(3, 8))
print(numbers)
#Note: Does not include last number, but includes first
print(range(20) == range(0, 20))
```

```py
#range can have a third argument,
#which determines the interval of the sequence produced, also called the step.
numbers = list(range(5, 20, 2))
print(numbers)
#Output: [5, 7, 9, 11, 13, 15, 17, 19]
#We can also create list of decreasing numbers,
#using a negative number as the third argument;
#for example list(range(20, 5, -2)).
```

```py
#You can import a module or object under a different name using the as keyword.
#This is mainly used when a module or object has a long or confusing name.
from math import sqrt as square_root
print(square_root(100))
```

ImportError: an import fails;
IndexError: a list is indexed with an out-of-range number;
NameError: an unknown variable is used;
SyntaxError: the code can't be parsed properly;
TypeError: a function is called on a value of an inappropriate type;
ValueError: a function is called on a value of the correct type, but with an inappropriate value.

```py
#The try block contains code that might throw an exception. If that exception occurs, the code in the try block stops being executed, and the code in the except block is run. If no error occurs, the code in the except block doesn't run.
try:
   num1 = 7
   num2 = 0
   print (num1 / num2)
   print("Done calculation")
except ZeroDivisionError:
   print("An error occurred")
   print("due to zero division")
   ```
   
```py
#To ensure some code runs no matter what errors occur, you can use a finally statement. The finally statement is placed at the bottom of a try/except statement. Code within a finally statement always runs after execution of the code in the try, and possibly in the except, blocks.
try:
   print("Hello")
   print(1 / 0)
except ZeroDivisionError:
   print("Divided by zero")
finally:
   print("This code will run no matter what")
```

```py
#You can raise exceptions by using the raise statement.
print(1)
raise ValueError
print(2)
#Output:
>>>
1
ValueError
>>>
```

```py
#Exceptions can be raised with arguments that give detail about them.
name = "123"
raise NameError("Invalid name!")
---
password = input("enter password")
if len(password) < 8:
 raise ValueError("password should be more than 8 characters")
 ```
 
 ```py
 #An assertion is a sanity-check that you can turn on or turn off when you have finished testing the program.
#An expression is tested, and if the result comes up false, an exception is raised.
#Assertions are carried out through use of the assert statement.
print(1)
assert 2 + 2 == 4
print(2)
assert 1 + 1 == 3
print(3)
>>>
1
2
AssertionError
>>>
```

```py
temp = -10
assert (temp >= 0), "Colder than absolute zero!"
>>>
AssertionError: Colder than absolute zero!
>>>
```

str.capitalize() <- only first character
str.center(width[,fillchar])
str.endswith(suffix[,start[,end]])
str.find(sub[,start[,end]])
str.lstrip([chars])
str.replace(old,new[,count])
str.lower()
str.rstrip([chars])
str.strip([chars])
str.upper()

```py
#EXTRA NOTES
try:
  print(1)
  print(20 / 0)
  print(2)
except ZeroDivisionError:
  print(3)
finally:
  print(4)

```