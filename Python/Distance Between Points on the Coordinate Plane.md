```py
#Calculate distance between two points in a coordinate plane

# Gather values

x, y = eval(input("Please enter the coordinates of your first point in the format 'x,y.' "))
X, Y = eval(input("Please enter the coordinates of your second point in the same format as the first. "))

#Calculate outcome

coordsD = ((X - x)**2 + (Y - y)**2 )**0.5

#Print the outcome

print("The distance between (", x, " , ", y, ") and (", X, " , ", Y, ") is ", coordsD, ".")
```