```py
#This program is a way to estimate pi using the summation method.
#Set le variables
n = eval(input("Please enter the number of times you want to run this program. Note that the lesser the faster, the more the slower. "))
s = 0

for i in range(1,n+1):
  if (i+1) % 2 == 0:
    sign = 1
  else:
    sign = -1
  s += sign/(2*i - 1)

pi = 4 * s

print("The estimated value of pi is ", pi, ".")
```