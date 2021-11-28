```py
#Ask the user for the starting numbers & inform & set variables
print("This program if for finding the GCF of any 2 numbers that the user provides.")

n1 = eval(input("Please enter your first number. "))
n2 = eval(input("Please enter your second number. "))

if n1 > n2:
  M = n1
  m = n2
else:
  M = n2
  m = n1

u = M % m

while u != 0:
  M = m
  m = u
  u = M % m

if u == 0:
  print("The GCF of ", n1, " and ", n2, " is ", m, ".")
  ```