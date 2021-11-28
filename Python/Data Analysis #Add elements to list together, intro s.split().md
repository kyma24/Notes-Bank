```py
s = input("enter the #s")
items = s.split()
#long string. Computer goes through items inside list of items.
#when hit the first non space item, record everything it finds. Example:
#s = a_bc_defg
#items = s.split()
#items[0] = a
#items[1] = bc
#items[2] = defg
#no more, so saves as list
l = [eval(x) for x in items]
#l becomes list of items
n = len(l)
#n contains the handy function that calculates how many elements are in the list
```