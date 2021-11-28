-   abstraction
    
    data abstraction provides the outside world with only essential information, in a process of representing essential features without including implementation details.
    
    A good real-world example is a _book_. When the term "book" is heard, don't know the exact specifics, such as page count, the color, or the size, but the idea, or abstraction of the book can be understood.
    
    The concept of abstraction is that we focus on essential qualities, rather than the specific characteristics of one particular example.
    
    In Java, abstraction is achieved using **abstract classes** and **interfaces**.
    
    An abstract class is defined using the **abstract** keyword.
    
    -   if a class is declared abstract it can't be instantiated(you can't create objects of that type)
    -   to use an abstract class, you have to inherit it from another class.
    -   Any class that contains an abstract method should be defined as abstract
    
    note: An abstract method is a method that is declared without an implementation(without braces, and followed by a semicolon): **abstract void walk();**
    
    A class containing an abstract method is an abstract class.
    
-   abstract class
    
    i.e. we can define Animal class as abstract:
    
    ```java
    abstract class Animal {
    	int legs = 0;
    	abstract void makeSound();
    }
    ```
    
    the makeSound method is also abstract, as it has no implementation in the superclass.
    
    We can inherit from the Animal class and define the makeSound() method for the subclass:
    
    ```java
    class Cat extends Animal {
    	public void makeSound() {
    		System.out.println("Meow");
    	}
    }
    ```
    
    every animal makes a sound, but each has a different way to do it. That's why an abstract class Animal is defined, and leave the implementation of how they make sounds to the subclasses. This is used when there is no meaningful definition for the method in the superclass.