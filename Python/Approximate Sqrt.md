```py
def sqrt(n):
  ng = 1
  lg = 0
  while abs(lg - ng) > 0.0000000000000000000001:
    lg = ng
    ng = (lg + (n/lg)) / 2
  return ng

n = eval(input("Please enter the number that you would lie to approx[sqrt]: "))
print("The approx[sqrt] of ",n," is ", sqrt(n))
```