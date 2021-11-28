```py
def max(i,j):
  if i >= j:
    return i
  elif i <= j:
    return j
  else:
    return j

i,j = eval(input("Type in the two numbers to find the max!(x,y) form. "))
k = max(i,j)
print("The larger number is", k)
```