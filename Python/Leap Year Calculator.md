```py
print("This program is to calculate whether or not a certain year is a leap year.")

#Get the year from the user
year = eval(input("Please enter a valid year. "))

#Calculate the state of the year(whether or not it is a leap year) and print results
if (year % 4 == 0) and not(year % 100 == 0) or (year % 400 == 0):
  print("This year is a leap year.")

else:
  print("This year is not a leap year.")
  ```