```py
#Open file on computer using open function
myfile = open("filename.txt")
#Sending "r" means open in read mode, which is the default.
#Sending "w" means write mode, for rewriting the contents of a file.
#Sending "a" means append mode, for adding new content to the end of the file.
#Adding "b" to a mode opens it in binary mode, which is used for non-text files (such as image and sound files).
# write mode
open("filename.txt", "w")

# read mode
open("filename.txt", "r")
open("filename.txt")

# binary write mode
open("filename.txt", "wb")

# after using file, need to close it
file = open("filename.txt", "w")
# do stuff to the file
file.close()
```

```py
#OPENING FILES

myfile = open("filename.txt")
#before file can be edited/read, it has to be opened
#argument of the open function is path to file. if file is in current working directory of program, you can specify only its name.


# w: write mode - rewrites contents of file
open("filename.txt", "w")

# r: open in read mode - default
open("filename.txt", "r")
open("filename.txt")

#a: append mode - adds new content to end of file
open("filename.tt", "a")

# b: binary write mode - adding b opens in binary mode, for non-text files
open("filename.txt", "wb")

#+ : adding plus sign gives extra access to files - i.e. below, r+ opens for both reading & writing
open("filename.txt", "r+")


#to close file after done:
file = open("filename.txt", "w")
# do stuff to the file
file.close()
```

```py
#READING FILES

file = open("filename.txt", "r")
cont = file.read()
print(cont)
file.close()
#contents of text file after being opened can be read using ".read" method
#above code will print all of the contents of filename.txt file


file = open("filename.txt", "r")
print(file.read(16))
print(file.read(4))
print(file.read(4))
print(file.read())
file.close()
#to read only certain amount of file, specify w/ number nested within parentheses. determines number of bytes that need to be read
#can make calls to read the file byte by byte: w/o any parameter or w/ a negative parameter inside the parentheses, will return entire contents


file = open("filename.txt", "r")
file.read()
print("Re-reading")
print(file.read())
print("Finished")
file.close()
#result
>>>
Re-reading

Finished
>>>
#after finishing reading, if you try to read again, it will return an empty string, since you are already done.


#retrieving each line in file: use readlines method - returns list where each element is a line in the file
file = open("filename.txt", "r")
print(file.readlines())
file.close()
#output:
>>>
['Line 1 text \n', 'Line 2 text \n', 'Line 3 text']
>>>

#can also use for loop to iterate through lines in file:
file = open("filename.txt", "r")

for line in file:
    print(line)

file.close()
#output:
>>>
Line 1 text

Line 2 text

Line 3 text
>>>
#print function auto-adds new line between lines(as shown above)
```

```py
#WRITING FILES

#write files using write method - writes string to file
file = open("newfile.txt", "w")
file.write("This has been written into a file")
file.close()

file = open("newfile.txt", "r")
print(file.read())
file.close()
#note: "w" mode will create a file if it doesn't already exist


#when file is opened in write mode, existing content is deleted
file = open("newfile.txt", "r")
print("Reading initial contents")
print(file.read())
print("Finished")
file.close()

file = open("newfile.txt", "w")
file.write("Some new text")
file.close()

file = open("newfile.txt", "r")
print("Reading new contents")
print(file.read())
print("Finished")
file.close()
#content of file will be overwritten


#write method: returns number of bytes written into a file(if successful)
msg = "Hello World!"
file = open("newfile.txt", "w")
amount_written = file.write(msg)
print(amount_written)
file.close()
#to write something of a data type other than a string, must be converted to a string first


#ASSIGNMENT: given a list of names: write into file, each in new line, and separately output them
names = ["John", "Oscar", "Jacob"]

file = open("names.txt", "w+")

n = len(names)
for i in range (0, n):
    file.write(names[i])
    file.write("\n")

file.close()


file= open("names.txt", "r")

print(file.read())

file.close()
```

```py
#WORKING WITH FILES

try:
   f = open("filename.txt")
   print(f.read())
finally:
   f.close()
#should avoid wasting resources by ensuring that file always closes. easy way to do so is to use try & finally. ensures that file always closes, whether or not an error occurs
#i.e. if you print 1/0 in the try section, the file is still going to close.


with open("filename.txt") as f:
   print(f.read())
#alternative is using with statement(s)
#creates temporary value, usually "f", that can only be accessed within the with statement; similar to for loop.
#file immediately closes after with is done, even if error occurs
```