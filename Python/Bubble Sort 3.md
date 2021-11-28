```py
def sort(a,b,c):
  if a > b:
    a,b = b,a 
  if b > c:
    b,c = c,b
  if a > b:
    a,b = b,a 
  return a,b,c

a,b,c = eval(input("Please enter the 3 numbers you want to sort in a,b,c format. "))
print("The ordering of your numbers from smallest to biggest is", sort(a,b,c))
```