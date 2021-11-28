```py
#Ask the user for the starting numbers & inform & set variables
print("This program is for finding the GCF of any 2 numbers that the user provides.")

num1 = eval(input("Please enter your first number."))
num2 = eval(input("Please enter your second number."))

i = 1

#Calculate
if num1 < num2:
  mini = num1
else:
  mini = num2

while i <= mini:
  if num1 % i == 0 and num2 % i == 0:
    gcf = i
  i = i + 1

print("The Grapest Cannon Factsor is", gcf)
```