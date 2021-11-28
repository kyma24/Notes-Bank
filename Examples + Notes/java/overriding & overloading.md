-   method overriding
    
    review: a subclass can define a behavior that's specific to the subclass type, meaning that a subclass can implement a parent class method based on its requirement.
    
    This feature is known as method **overriding**.
    
    ```java
    //i.e.
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
    ```
    
    in the above code, the Cat class overrides the **makeSound()** method of its superclass Animal.
    
    **Rules for Method Overriding**:
    
    -   should have the **same** return type and arguments
    -   the **access level** can't be more restrictive than the overriden method's access level(i.e. if the superclass method is declared public, the overriding method in the sub class can neither be private nor protected)
    -   a method declared **final** or **static** can't be overriden
    -   if a method can't be inherited, it can't be overriden
    -   constructors can't be overriden
    
    note: method overriding is also known as **runtime polymorphism**.
    
-   method overloading
    
    when methods have the same name but different parameters, it is known as method overloading.
    
    This can be very useful when you need the same method functionality for different types of parameters.
    
    ```java
    //i.e. method that returns the maximum of 2 parameters
    int max(int a, int b) {
    	if(a > b) {
    		return a;
    	}
    	else {
    		return b;
    	}
    }
    ```
    
    the method shown will only work for parameters of type integer.
    
    However, might want to use it for doubles, as well. For that, need to overload max method:
    
    ```java
    double max(double a, double b) {
    	if(a > b) {
    		return a;
    	}
    	else {
    		return b;
    	}
    }
    ```
    
    now max method will also work with doubles.
    
    An overloaded method must have a different argument list; the parameters should differ in their type, number, or both.
    
    note: Another name for method overloading is **compile-time polymorphism**.
    
    ```java
    class A {
       public void doSomething() {
         System.out.println("A");
       }
       public void doSomething(String str) {
         System.out.println(str);
       }
    }
    class B {
       public static void main(String[ ] args) {
       A object = new A();
       object.doSomething("B");
       }
    }
    
    // prints B
    ```