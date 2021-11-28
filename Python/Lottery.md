```py
#Do the importing
import random

#Get the guess
i = random.randint(0,99)
guess = eval(input("Type in your guess for the lottery! "))

guessB = guess % 10
guessC = guess // 10
guessD = i % 10
guessE = i // 10

#Do the analyzing/outputting
if guess == i:
  print("Congrats! You've won the lottery! You earned... $10,000!")

elif guessB == guessE and guessC == guessD:
  print("Congrats! You've gotten the right digits of the lottery number, but not the right order! You earned... $3,000!")

elif guessB == guessD or guessC == guessE:
  print("Congrats! You've matched one digit! You earned... $1,000!")

elif guessB == guessE or guessC == guessD:
  print("Congrats! You've matched one digit! You earned... $1,000!")

else:
  print("Oops, sorry! You've gotten none of the digits. Try again next time!")

print(i)
```