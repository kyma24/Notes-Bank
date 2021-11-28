```py
# This program is to find the least amount of coins in a certain amount of money

#Get the 'certain amount of money'

C = eval(input("Please input the amount of money that you want to translate into the smallest amount of coins in the format X.XX. " ))

C = C*100

#Calculate

dollars = C // 100
change = C % 100

quarters = change // 25
change1 = change % 25

dimes = change1 // 10
change2 = change1 % 10

nickels = change2 // 5
change3 = change2 % 5

pennies = round(change3)

#Print out results

print("The change due is ", dollars, " dollars, ")
print(quarters, " quarters, ")
print(dimes, " dimes, ")
print(nickels, " nickels,")
print("and ", pennies, " pennies.")
```