`public keyword:`

```java
public static void main(String[] args)
```

`public is an access modifier: it is used to set the level of access. You can use access modifiers for classes, attributes, and methods`

`**for classes**, the available modifiers are public or default(left blank), as described below:`

-   **public**: The class is accessible by any other class
-   **default**: the class is accessible only by classes in the same package

`the following choices are available **for attributes & methods**:`

-   **default**: A variable or method declared w/ no access control modifier is available to any other class in the same package
-   **public**: Accessible from any other class
-   **protected**: Provides the same access as the default access modifier, w/ the addition that subclasses can access protected methods and variables of the _superclass_
-   **private**: Accessible only w/in the declared class itself

i.e.

```java
public class Vehicle
{
	private int maxSpeed;
	private int wheels;
	private String color;
	private double fuelCapacity;

	public void horn()
	{
		System.out.println("beep!");
	}
}
```

note: it's best to keep the variables w/in the class private. The variables are accessible and modified using getters and setters.

-   getters & setters
    
    \*\*`Getters** and **Setters** are used to efficiently protect your data, particularly when creating classes. For each var, **get** method returns value, while set method **sets** value.`
    
    -   **getters** start w/ **get**, followed by var name, w/ the 1st letter of var name _CAPITALIZED_
        -   the variable in getColor is _lowercase_ color, as for anything else as well
    -   **setters** start w/ **set**, followed by var name, w/ the 1st letter of the var name _CAPITALIZED_
    
    i.e.
    
    ```java
    public class Vehicle
    {
    	private String color;
    
    	//Getter
    	public String getColor()
    	{
    		return color;
    	}
    
    	//Setter
    	public void setColor(String c)
    	{
    		this.color = c;
    	}
    }
    ```
    
    -   **getter** method returns val of attribute
    -   **setter** method takes a parameter and assigns it to the attribute
        -   i.e. in Nitro Type, when you recolor your car(or buy one for the first time), you either set the color or get the default color; this is when you use the setter method
    
    The keyword **this** is used to refer to the current object. Basically, **this.color** is the **color** attribute of the current object.← _referring to the definition of the attribute_
    
    -   current object = the variable w/ the current instance of the object(referred to in the class)
    
    `once getter and setters have been defined, we can use it in **main**`
    
    ```java
    public static void main(String[] args)
    {
    	Vehicle v1 = new Vehicle();
    	v1.setColor("Red");
    	System.out.println(v1.getColor());
    }
    ```
    
    -   getters and setters allow us to have ctrl over the values. You may, for example, validate the given value in the setter before actually setting the value
        -   doing things accordingly based on the input, i.e. in a math class app, for a dividing function, if someone inputs 0 as the denominator, you can consider returning an exception
    
    Getters & setters are fundamental building blocks for **encapsulation**
    
-   constructors
    
    \*\*`constructors** are special methods called(invoked) when an instance of an object is created and are used to assign a value to the attributes(initialize) of the object.`
    
    `it can be used to provide initial values for object attributes`
    
    -   a constructor name must be the **same** as its **class name**
    -   a constructor must have no explicit return type(no specification like int, String, etc)
    
    i.e.
    
    ```java
    public class Vehicle
    {
    	private String color;
    	Vehicle()
    	{
    		color = "Red";
    	}
    }
    ```
    
    -   **Vehicle**() method is the constructor of our class, so whenever an object of that class is created, the color attribute will be set to "Red".
    -   A constructor can also take parameters to initialize attributes
    
    ```java
    public class Vehicle
    {
    	private String color;
    	Vehicle(String c)
    	{
    		color = c;
    	}
    }
    ```
    
    -   constructors can be thought of as methods that will set the default of your class, so you don't need to repeat the same code every time
    
    ```java
    public class MyClass {
      public static void main(String[ ] args) {
        Vehicle v = new Vehicle("Blue");
      }
    }
    //constructor called when create an boject using new keyword
    //sets color attribute to blue
    ```
    
    ```java
    //a single set can have multiple constructors w/ any number of parameters
    //setter methods inside the constructors can be used to set attribute values
    public class Vehicle {
      private String color;
    
      Vehicle() {
        this.setColor("Red");
      }
      Vehicle(String c) {
        this.setColor(c);
      }
    
      // Setter
      public void setColor(String c) {
        this.color = c;
      }
    }
    //2 constructors above: one w/o any parameters to set color to red, the other accepts a parameter and assigns to attribute
    //using constructors to create
    
    //color will be red
    Vehicle v1 = new Vehicle();
    
    //color will be green
    Vehicle v2 = new Vehicle("Green");
    
    //each Java class has a default constructor whether or not you have done anything yet
    ```