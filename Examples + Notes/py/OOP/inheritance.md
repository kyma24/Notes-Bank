inheritance provides a way to share functionality between classes.

imagine several classes, **Cat**, **Dog**, **Rabbit** and so on. Although they may differ in some ways(only **Dog** might have the method **bark**), they are likely to be similar in others(all having the attributes **color** and **name**)

this similarity can be expressed by making them all inherit from a **superclass Animal**, which contains the shared functionality

to inherit a class from another class, put the superclass name in parentheses after the class name

```python
#i.e.
class Animal:
	def __init__(self, name, color):
		self.name = name
		self.color = color

class Cat(Animal):
	def purr(self):
		print("Purr...")

class Dog(Animal):
	def bark(self):
		print("Woof!")

fido = Dog("Fido", "brown")
print(fido.color)
fido.bark()
```

a class that inherits from another class is called a **subclass**.

a class that is inherited from is called a **superclass**.

if a class inherits from another with the same attributes or methods, it overrides them.

```python
class Wolf:
	def __init__(self, name, color):
		self.name = name
		self.color = color

	def bark(self):
		print("Grr...")

class Dog(Wolf):
	def bark(self):
		print("Woof")

husky = Dog("Max", "grey")
husky.bark()
#in this example, Wolf is the superclass, Dog is the subclass
```

```python
class A:
  def method(self):
    print(1)

class B(A):
  def method(self):
    print(2)

B().method()

#will print 2
```

inheritance can also be indirect. one class can inherit from another, and that class can inherit from a third class.

```python
class A:
	def method(self):
		print("A method")

class B(A):
	def another_method(self):
		print("B method")

class C(B):
	def third_method(self):
		print("C method")

c = C()
c.method()
c.another_method()
c.third_method()
```

however, note that circular inheritance is not possible.

```python
#i.e.
class A:
	def a(self):
		print(1)

class B(A):
	def a(self):
		print(2)

class C(B):
	def c(self):
		print(3)

c = C()
c.a()
#will print 2
```

the function **super** is a useful inheritance-related function that refers to the parent class. It can be used to find the method with a certain name of an object's superclass

```python
class A:
	def spam(self):
		print(1)

class B(A):
	def spam(self):
		print(2)
		super().spam()

B().spam()

#super().spam() calls the spam method of the superclass
```