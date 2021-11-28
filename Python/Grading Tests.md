```py
s = input("Enter the grades. ")
grades = s.split()
l = [eval(x) for x in grades]
n = len(l)

for i in range (n):
  if l[i] >= 90:
    grade = "A"
  elif l[i] >= 80:
    grade = "B"
  elif l[i] >= 70:
    grade = "C"
  elif l[i] >= 60:
    grade = "D"
  else:
    grade = "F"
  print("Student ", i+1, " has a letter grade of ", grade, ".")
  ```