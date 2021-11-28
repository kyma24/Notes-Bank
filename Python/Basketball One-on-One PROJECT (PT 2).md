Now we calculate the scores of each individual player.
```py
s = input("Enter the score of the game. ")
n = len(s)
acount = 0
bcount = 0
for i in range (n):
  if s[i] == "A":
    acount += int(s[i+1])
  elif s[i] == "B":
    bcount += int(s[i+1])
print("The score of A is", acount, ". The score of B is", bcount, ".")
```