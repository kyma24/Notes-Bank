an interface is a completely abstract class that contains only abstract methods.

Some specifications for interfaces:

-   defined using the **interface** keyword
-   may contain only static final variables
-   cannot contain a constructor because interfaces can't be instantiated
-   interfaces can extend other interfaces
-   a class can implement any number of interfaces

```java
//i.e.
interface Animal {
	public void eat();
	public void makeSound();
}
```

interfaces have the following properties:

-   an interface is implicitly abstract. Don't need to use the abstract keyword while declaring an interface
-   each method in an interface is also implicitly abstract, so the abstract keyword is not needed
-   methods in an interface are implicitly public

note: a class can inherit from just one superclass, but can implement multiple interfaces

use the **implements** keyword to use an interface with the class.

```java
interface Animal {
	public void eat();
	public void makeSound();
}

class Cat implements Animal {
	public void makeSound() {
		System.out.println("Meow");
	}
	public void eat() {
		System.out.println("omnomnom");
	}
}
```

when implementing an interface, need to override all of the methods.