```py
print("This program is to find the number of prime integers under/including a given number.")
n = eval(input("Please enter the said number. "))
k = 3
count = 1

while k <= n:
  f = 2
  prime = True
  while f < k:
    if k % f == 0:
      prime = False
    f += 1
  if prime == True:
    count += 1
  k += 1
  
print("The number of primes under/equal to ",n," is ", count,".")
```