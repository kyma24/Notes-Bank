__Requirements:__
You have been asked to make a special book categorization program, which assigns each book a special code based on its title.

The code is equal to the first letter of the book, followed by the number of characters in the title.

For example, for the book "Harry Potter", the code would be:

**H12** , as it contains 12 characters (including the space).

You are provided a **books.txt** file, which includes the book titles, each one written on a separate line.

Read the title one by one and output the code for each book on a separate line.

For example, if the books.txt file contains:

Some book

Another book

Your program should output:

S9

A12

NOTE: the **readlines()** method, which returns a list containing the lines of the file.

Also, remember that all lines, except the last one, contain a **\\n** at the end, which should not be included in the character count.

```py
file = open("/usercode/files/books.txt", "r")

fill = file.readlines()
length = len(fill)

#print(fill)


for i in range (0, length):
    if i < length - 1:
        print(fill[i][0] + str(len(fill[i]) - 1))
        #since Strings are lists, fill[i][0] takes the 0th character of the i'th term of the fill list
        #str() method turns data type into string
        #minus one bc spaces don't count when doing this
    else:
        print(fill[i][0] + str(len(fill[i])))

#take length of list! put in for loop.
#if index of item in list is less than total length, minus three
#^bc it auto-includes the extra " \n" at the end(w/ a space!)
#and then do what you always do: find the 0th index for the 1st char

file.close()
```