```py
import random
n1 = random.randint(0,9)
n2 = random.randint(0,9)
answer = eval(input("What is " + str(n1) + " + " + str(n2) + "? "))
print(n1," + ",n2," = ", answer, "is ", n1 + n2 == answer)
```