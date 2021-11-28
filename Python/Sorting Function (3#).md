```py
def sort(a,b,c):
  if a >= b >= c:
    big = a
    smol = b
    mini = c
  elif a >= c >= b:
    big = a
    smol = c
    mini = b
  elif b >= a >= c:
    big = b
    smol = a 
    mini = c
  elif b >= c >= a:
    big = b
    smol = c
    mini = a 
  elif c >= a >= b:
    big = c
    smol = a 
    mini = b
  else:
    big = c
    smol = b
    mini = a
  return mini,smol,big

a,b,c = eval(input("Please enter the 3 numbers you want to sort in a,b,c format. "))
print("The ordering of your numbers from smallest to biggest is", sort(a,b,c))
```