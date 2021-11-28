refers to the idea of "having many forms". Occurs when there is a hierarchy of classes related to each other through inheritance.

A call to a member method will cause a different implementation to be executed, depending on the type of the object invoking the method.

Example: **Dog** and **Cat** are classes that inherit from the **Animal** class. Each class has its own implementation of the **makeSound()** method.

```java
class Animal {
	public void makeSound() {
		System.out.println("Grr...");
	}
}
class Cat extends Animal {
	public void makeSound() {
		System.out.println("Meow");
	}
}
class Dog extends Animal {
	public void makeSound() {
		System.out.println("Woof");
	}
}
```

As all **Cat** and **Dog** objects are **Animal** objects, the following can be done in main:

```java
public static void main(String[] args) {
	Animal a = new Dog();
	Animal b = new Cat();
}
```

two reference variables of type Animal have been created, and pointed to the **Cat** and **Dog** objects.

Now, able to call the makeSound() methods:

```java
a.makeSound();

b.makeSound();
```

as the reference variable **a** contains a Dog object, the makeSound() method of the Dog class will be called.

The same applies to the **b** variable.

note: This demonstrates that it is possible to use the **Animal** variable without actually knowing that it contains an object of the subclass.

This is very useful when there are multiple subclasses of the superclass.

conclusion: polymorphism is one method, with different implementations.