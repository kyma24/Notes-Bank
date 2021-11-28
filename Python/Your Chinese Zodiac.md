```py
#first get the year from the user
year = eval(input("Please enter your birth year. "))

#calculate zodiac animal
p = year % 12

if p == 3:
  print("Your Chinese Zodiac is the Pig.")

elif p == 4:
  print("Your Chinese Zodiac is the Rat.")

elif p == 5:
  print("Your Chinese Zodiac is the Ox.")

elif p == 6:
  print("Your Chinese Zodiac is the Tiger.")

elif p == 7:
  print("Your Chinese Zodiac is the Rabbit.")

elif p == 8:
  print("Your Chinese Zodiac is the Dragon.")

elif p == 9:
  print("Your Chinese Zodiac is the Snake.")

elif p == 10:
  print("Your Chinese Zodiac is the Horse.")

elif p == 11:
  print("Your Chinese Zodiac is the Sheep.")

elif p == 0:
  print("Your Chinese Zodiac is the Monkey.")

elif p == 1:
  print("Your Chinese Zodiac is the Rooster.")

elif p == 2:
  print("Your Chinese Zodiac is the Dog.")

else:
  print("Your Chinese Zodiac is the Cat.")
```