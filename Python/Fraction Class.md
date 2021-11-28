```python
class Fraction:
    def __init__(self,top,bottom):
        self.num = top
        self.den = bottom
	def show(self): # to display fraction
    	print(self.num,"/",self.den)
	def __str__(self): # to print fraction
    	return str(self.num)+"/"+str(self.den)
	def __add__(self,otherfraction): # to add fractions & simplify
    	newnum = self.num*otherfraction.den + self.den*otherfraction.num
    	newden = self.den * otherfraction.den
    	common = gcd(newnum,newden)
    	return Fraction(newnum//common,newden//common)
```

instance of `Fraction` class
![../_images/fraction1.png](https://runestone.academy/runestone/books/published/pythonds/_images/fraction1.png)

instance of `Fraction` class with 2 methods
![../_images/fraction2.png](https://runestone.academy/runestone/books/published/pythonds/_images/fraction2.png)

The `Fraction` object now has 2 very useful methods & looks like above. A additional group of methods that we need to include in the `Fraction` class will allow 2 fractions to compare themselves to one another. Assume we have 2 `Fraction` objects, `f1` and `f2`. `f1 == f2` will only be `True` if they are references to the same object. Two different objects w/ the same numerators and denominators wouldn't be equal under this implementation. This is called **shallow equality**.
![../_images/fraction3.png](https://runestone.academy/runestone/books/published/pythonds/_images/fraction3.png)

We can create **deep equality** - equality by the same value, not the same referrence - by overriding the `__eq__` method. the `__eq__` method is another standard method available in any class. The `__eq__` method compares 2 objects & returns `True` if their values are the same, `False` otherwise.

In `Fraction` class, can implement the `__eq__` method by again putting the two fractions in common terms and then comparing the numerators. It is important to note that there are other relational operators that can be overriden, like `__le__`(the less than or equal to function).
```python
def __eq__(self, other):
	firstnum = self.num * other.den
	secondnum = other.num * self.den
	
	return firstnum == secondnum
```

Complete fraction class:
```python
def gcd(m,n):
    while m%n != 0:
        oldm = m
        oldn = n

        m = oldn
        n = oldm%oldn
    return n

class Fraction:
     def __init__(self,top,bottom):
         self.num = top
         self.den = bottom

     def __str__(self):
         return str(self.num)+"/"+str(self.den)

     def show(self):
         print(self.num,"/",self.den)

     def __add__(self,otherfraction):
         newnum = self.num*otherfraction.den + \
                      self.den*otherfraction.num
         newden = self.den * otherfraction.den
         common = gcd(newnum,newden)
         return Fraction(newnum//common,newden//common)

     def __eq__(self, other):
         firstnum = self.num * other.den
         secondnum = other.num * self.den

         return firstnum == secondnum

x = Fraction(1,2)
y = Fraction(2,3)
print(x+y)
print(x == y)
```