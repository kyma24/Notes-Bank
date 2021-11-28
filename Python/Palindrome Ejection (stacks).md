```py
#stackClass.py
class Stack:
    def __init__(self):
        self.stack = []
    
    def Pop(self):
        if not self.stack:
            return None
        else:
            return self.stack.pop()
    
    def push(self, object):
        return self.stack.append(object)
    
    def size(self):
        return len(self.stack)

    def peek(self):
        if not self.stack:
            return None
        else:
            return self.stack[-1]
    
    def isEmpty(self): 
        return not self.stack
```
```py
#main.py
from stackClass import Stack

pal = input("Input a value to be ejected. ")
stack = Stack()

for i in range(len(pal)):
    stack.push(pal[i])

reversePal = ""

while not stack.isEmpty():
    reversePal += stack.Pop()

if pal == reversePal:
    print("The value", pal, "is a palindrome.")
else:
    print("The value", pal, "is not a palindrome. Its reverse is", reversePal, ".")
```