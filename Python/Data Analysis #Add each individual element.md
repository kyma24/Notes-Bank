```py
#User input 6 numbers, program find average of numbers and how many numbers are gr8er than the average
n = 6
numbers = [ ]
#temp variable since finding average of numbers
s = 0
#read in values with for loop
for i in range (n):
  v = eval(input("Enter a number in your list. "))
  #add the variable into the list, update the sum
  numbers.append(v)
  s += v
average = s/n
#now that have average, count how many ints are above average
count = 0
for i in range (n):
  if numbers [i] > average:
    count += 1

print("The average of your set of 6 numbers is ", average,
". The number of elements in your set above the average is ", count, ".")
```