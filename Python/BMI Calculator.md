```py
# This is a simple program to calculate your Body Mass Index, or BMI, based on your weight and height. Example: 94 pounds and 58.5 inches

#Gather information from the user
h = eval(input("Please type in your height in inches. "))
w = eval(input("Please type in your weight in pounds. "))

#Convert to appropriate measurements to calculate the BMI
m = h * 0.0254
kg = w * 0.45359237

#Calculate BMI
BMI = kg / m**2

#Evaluate the state of the user(Overweight, average, etc.)
if BMI < 18.5:
  print("Your BMI is ", BMI, ", which is considered underweight.")

elif BMI < 25:
  print("Your BMI is ", BMI, ", which is considered healthy.")

elif BMI < 30:
  print("Your BMI is ", BMI, ", which is considered overweight.")

else:
  print("Your BMI is ", BMI, ", which is considered obese.")
  ```