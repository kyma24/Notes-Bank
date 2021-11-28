-   object-oriented programming(OOP)
    
    -   programming style intended to make thinking abt programming more like the real world
    -   in OOP, each object is unique.
    -   OOP: three dimensions of the object - identity, attributes, and behavior.
        -   attributes describe object's current state(or characteristics)
        -   behavior demonstrates what object is capable of doing(i.e. method)
    -   class describes what object will be, but not object itself(blueprint, descriptions, or definitions for object). Can use same class as blueprint for creating multiple objects.
        -   step one: define class, then becomes blueprint for object creation.
        -   each class has name, which is used to define attributes and behavior.
            -   example of attributes: name, height, weight, gender, age
            -   example of behavior: walk, run, jump, speak, sleep
    -   object is an instance of a class
-   methods
    
    -   methods define behavior
        -   collection of statements that are grouped together to perform an operation(i.e. System.out.println = method)
    -   can define own method!
    
    ```java
    class MyClass
    {
    	static void sayHello()
    	{
    		System.out.println("Hello World!");
    	}
    
    	public static void main(String[] args)
    	{
    		sayHello();
    	}
    }
    ```
    
    -   above calls method sayHello()
        
    -   to call method, type name and follow the name w/ set of parentheses.
        
    -   when method runs, code jumps down to where method is defined, executes code inside, then goes back & proceeds
        
        -   method can be located anywhere(don't define method inside main method. however, can define private class inside class)
    -   method parameters
        
        -   can also create a method that takes parameters along w/ it when you call it. Write parameters within method's parentheses.
            
            -   i.e. we can modify sayHello()to take and output a String parameter →
            
            ```java
            static void sayHello(String name)
            {
            	System.out.println("Hello" + name);
            }
            ```
            
            -   above: takes String called name as parameter, used in method's body. When calling method, we pass the parameter value inside the parentheses. Methods can take multiple(comma-separated) parameters. ← definition of the method is called a signature
    -   method return types
        
        ```java
        static int sum(int val1, int val2) {
           return val1 + val2;
        }
        ```
        
        -   if don't want method to return anything, use keyword **void**
        -   Java method = Python function
        
        ```java
        class MyClass
        {
        	static int sum(int val1, int val2)
        	{
        		return val1 + val2;
        	}
        
        	public static void main(String[] args)
        	{
        		int x = sum(2,5);
        		System.out.println(x);
        	}
        }
        ```
        
        -   as method returns value, can assign to variable
        
        ```java
        // returns an int value 5
        static int returnFive() {
          return 5;
        }
        
        // has a parameter
        static void sayHelloTo(String name) {
          System.out.println("Hello " + name);
        }
        
        // simply prints"Hello World!"
        static void sayHello() {
          System.out.println("Hello World!");
        }
        ```
        
        ```java
        public static void main(String[] args)
        {
        	int res = max(7,42);
        	System.out.println(res); //42
        }
        
        static int max(int a, int b)
        {
        	if(a > b)
        	{
        		return a;
        	}
        	else
        	{
        		return b;
        	}
        }
        ```
        
        -   a method can have one type of parameter(or parameters) and return a different type. i.e. it can take 2 doubles & return an int.
-   creating classes
    
    you know what to do...
    
    just create a new class on eclipse or something ;)
    
-   creating objects
    
    ```java
    class MyClass
    {
    	public static void main(String[] args)
    	{
    		Animal dog = new Anrimal();
    		dog.bark();
    	}
    }
    ```
    
    -   dog is an object of type Animal. Thus we can call its bark() method, using name of object & period. Period notation used to access object's attributes & methods.
    -   adding onto Animal class w/ bark method
-   class attributes
    
    `attributes = variables within a class`
    
    ```java
    public class Vehicle
    {
    	int maxSpeed;
    	int wheels;
    	String color;
    	double fuelCapacity;
    
    	void horn
    	{
    		System.out.println("Beep!");
    	}
    }
    ```
    
    -   `maxSpeed, wheels, color, and fuelCapacity are the attributes of the Vehicle class, and horn() is the only method`
        
    -   creating objects in class
        
        `adding onto the class Vehicle:`
        
        ```java
        class MyClass
        {
        	public static void main(String[] args)
        	{
        		Vehicle v1 = new Vehicle();
        		Vehicle v2 = new Vehicle();
        		v1.color = "red";
        		v2.horn();
        	}
        }
        ```
        
        `can create multiple objects of Vehicle class, and use the dot syntax to access their attributes & methods`
        

```java
public class A
{
	public void test()
	{
		System.out.println("Hi");
	}
}

class B
{
	public static void main(String args[])
	{
		A obj = new A();
		obj.test();
	}
}
```