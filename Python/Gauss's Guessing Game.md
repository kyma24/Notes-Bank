```py
import random

number = random.randint(0,100)

print("Guess le magic numero btwn 0 and 100.")

guess = -19849384

while guess != number:
  
  guess = eval(input("Plush eentre le ze gus "))

  if guess == number:
    print("Yas, le numero eesh",number)

  elif guess > number:
    print("Yop, u has a guess 2 hi")

  else:
     print("Yoop, ur gauss es lolo")
```