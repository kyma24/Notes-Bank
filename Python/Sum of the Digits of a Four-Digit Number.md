```py
#This is a program to calculate the sum of the digits of a 4-digit number.


#Retrieve the number

fourDigit = eval(input("Please input a four-digit number."))

#Calculate first digit

digitI = fourDigit // 1000

#Calculate second digit

digitII = (fourDigit % 1000) // 100

#Calculate third digit

digitIII = (fourDigit % 1000) % 100 // 10

#Calculate units digit

digitIV = ((fourDigit % 1000) % 100) % 10

#Give result
totalSum = digitI + digitII + digitIII + digitIV
print("The sum of the digits of your four-digit number is ", totalSum, ".")
```