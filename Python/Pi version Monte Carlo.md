```py
#This program is a Monte Carlo simulation to find the approximate value of pi.
import random
n = eval(input("How many times would you like to run the Monte Carlo's Pies simulation? Note: The more times, the more accurate, but it will be slower. "))
i = 1
for i in range (1, n+1):
  hit = 0
  y = random.random() * 2 - 1
  x = random.random() * 2 - 1
  D = (x**2 + y**2 )**0.5
  if D < 1:
    hit += 1

bleh = (hit / n) * 4

print("The estimate of Pi using the Monte Carlo simulation ",n," times is ",bleh, ".")
```