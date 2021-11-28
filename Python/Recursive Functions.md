```py
def g(x):
  if x > 0:
    return g(x-3) + 1
  else:
    return 3*x

x = eval(input("Please enter the number. "))
print("The output of the function with a value of", x, "is", g(x), ".")

def f(x,y):
  if x > y:
    return f(x-y,y-1) + 2
  else:
    return x + y

x = eval(input("Please enter the first input. "))
y = eval(input("Please enter the second input. "))
print("The output of the function f(x,y) is", f(x,y), ".")

def h(x):
  if x > 5:
    return h(x-7)+1
  elif x >= 0:
    return x
  else:
    return h(x+3)
x = eval(input("Please enter the number. "))
print("The output of the function is", h(x), ".")
```