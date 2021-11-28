this is the process that enables one class to acquire the properties(methods and variables) of another. With inheritance, the information is placed in a more manageable, hierarchical order.

The class inheriting the properties of another is the **subclass**(also called derived class, or child class); the class whose properties are inherited is the **superclass**(base class, or parent class).

To inherit from a class, use the **extends** keyword.

```java
//i.e. have class Dog inherit from class Animal
class Dog extends Animal {
	// some code
}

//Dog is subclass, Animal is superclass
```

when one class is inherited from another class, it inherits all of the superclass' **non-private** variables and methods.

```java
//i.e.
class Animal {
	protected int legs;
	public void eat() {
		System.out.println("Animal eats");
	}
}

class Dog extends Animal {
	Dog() {
		legs = 4;
	}
}
```

as seen, the Dog class inherits the legs variable from the Animal class. Can now declare a Dog object and call the **eat** method of its superclass:

```java
class MyClass {
	public static void main(String[] args) {
		Dog d = new Dog();
		d.eat();
	}
}
```

**protected** access modifier makes members visible to only the subclasses.

Constructors aren't member methods, and so aren't inherited by subclasses.

However, the constructor of the superclass is called when the subclass is instantiated.

```java
class A {
	public A() {
		System.out.println("New A");
	}
}
class B extends A {
	public B() {
		System.out.println("New B");
	}
}

class Program {
	public static void main(String[] args) {
		B obj = new B();
	}
}
```

can access the superclass from the subclass using the **super** keyword.

i.e. **super.var** accesses the var member of the superclass