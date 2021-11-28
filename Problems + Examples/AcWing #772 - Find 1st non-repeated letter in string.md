If there is no letter that isn't repeated, output `no`. Otherwise, return the first-occuring letter that isn't repeated.

My way:
```python
def unique(x):
    l = [0]*len(x)
    i = 0
    for char in x:
        l[i] = ord(char)
        i += 1
    a = [0]*len(x)
    j = 0
    for char in x:
        a[j] = ord(char)
        j += 1
    a.sort()
    b = []
    count = 0
    for i in range(len(a)):
        if i == 0:
            if a[i] != a[i+1]:
                b.append(a[i])
                count += 1
        elif i == len(a)-1:
            if a[i] != a[i-1]:
                b.append(a[i])
                count += 1
        else:
            if a[i] != a[i+1] and a[i] != a[i-1]:
                b.append(a[i])
                count += 1
    if count > 1:
        c = [0]*count
        for i in range(count):
            c[i] = l.index(b[i])
        c.sort()
        return chr(l[c[0]])
    elif count == 1:
        return chr(b[0])
    else:
        return "no"

def main():
    l = input()
    print(unique(l))
    
main()
```

Better way:
```python
s = input()

c = [0]*26

for i in s:
    c[ord(i) - ord("a")] += 1

found = False      
for i in s:
    if c[ord(i) - ord("a")] == 1:
        found = True
        print (i)
        break

if not found:
    print ("no")
```

Or:
- Start at the end of the string, iterate backward
- Keep a hash map as in the video with the number of occurrences
- Also keep a single character which represents the last encountered letter
- In the loop: 
1. If the character has been seen already (hash map not zero) add 1 and continue
2. Of the character has NOT been seen already (hash map is zero) add 1, update the “last seen” character, and continue
- This way, we skip all the repeated characters once they are logged
- Once we get to the end of the loop, if the count of the “last seen” character is 1, then return that character (I.e. it was unique and closest to the start) otherwise return underscore