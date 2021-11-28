```py
#This program predicts the person's birth day based on their responses to a few questions.

print("Hi there! This program predicts your birth day! Answer some questions and we'll tell you!")

question1 = "Is your birth day one of these? \n" + \
"1 3 5 7 \n" + \
"9 11 13 15 \n" + \
"17 19 21 23 \n" + \
"25 27 29 31 \n" + \
"Enter 0 for No and 1 for Yes. "

question2 = "Is your birth day one of these? \n" + \
"2 3 6 7 \n" + \
"10 11 14 15 \n" + \
"18 19 22 23 \n" + \
"26 27 30 31 \n" + \
"Enter 0 for No and 1 for Yes. "

question3 = "Is your birth day one of these? \n" + \
"4 5 6 7 \n" + \
"12 13 14 15 \n" + \
"20 21 22 23 \n" + \
"28 29 30 31 \n" + \
"Enter 0 for No and 1 for Yes. "

question4 = "Is your birth day one of these? \n" + \
"8 9 10 11 \n" + \
"12 13 14 15 \n" + \
"24 25 26 27 \n" + \
"28 29 30 31 \n" + \
"Enter 0 for No and 1 for Yes. "

question5 = "Is your birth day one of these? \n" + \
"16 17 18 19 \n" + \
"20 21 22 23 \n" + \
"24 25 26 27 \n" + \
"28 29 30 31 \n" + \
"Enter 0 for No and 1 for Yes. "

num = 0

answer = eval(input(question1))
if answer == 1:
  num = num + 1

answer = eval(input(question2))
if answer == 1:
  num = num + 2

answer = eval(input(question3))
if answer == 1:
  num = num + 4

answer = eval(input(question4))
if answer == 1:
  num = num + 8

answer = eval(input(question5))
if answer == 1:
  num = num + 16

print("We have predicted that your birth day is ", num, "!")
```