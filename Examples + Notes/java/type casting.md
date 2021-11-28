-   casting
    
    assigning a value of one type to a variable of another type is known as **Type Casting**.
    
    To cast a value to a specific type, place the type of parentheses and position it in front of the value.
    
    ```java
    int a = (int) 3.14;
    System.out.println(a);
    ```
    
    the code above is casting the value 3.14 to an integer, with 3 as the resulting value.
    
    ```java
    //i.e.
    double a = 42.571;
    int b = (int) a;
    System.out.println(b);
    ```
    
    note: Java supports automatic type casting of integers to floating points, since there is no loss of precision.
    
    On the other hand, type casting is mandatory when assigning floating point values to integer variables.
    
    Just gets rid of everything past the decimal point.
    

## Type Casting

For classes, there are two types of casting.

### Upcasting

You can cast an instance of an instance of a subclass to its superclass.

Consider the following example, assuming that Cat is a subclass of Animal.

```java
Animal a = new Cat();
```

Java automatically upcasted the Cat type variable to the Animal type.

### Downcasting

Casting an object of a superclass to its subclass is called **downcasting**.

```java
Animal a = new Cat();
((Cat)a).makeSound();
```

This will try to cast the variable a to the **Cat** type and call its makeSound() method.

Why is upcasting automatic, downcasting manual? Bc upcasting can never fail. But if have a group of different Animals and want to downcast them all to a Cat, then there's a chance that some of these Animals are actually Dogs, so the process fails.