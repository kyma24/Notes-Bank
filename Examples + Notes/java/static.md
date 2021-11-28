-   for memory management
    
    i.e. if we have circle method, we only need 1 set, unchangeable variable/reference of the constant pi. By declaring this static, it will save space.
    
-   for variables
    
    when you declare a variable or a method as static, it belongs to the class rather than to a specific instance. This means that only 1 instance of a static method exists, even if you create multiple objects of the class, or if you don't create any. it will be shared by all objects.
    
    ```python
    public class Counter {
    	public static int COUNT = 0;
    	Counter() {
    		COUNT++;
    	}
    }
    ```
    
    COUNT variable will be shared by all objects of that class. Now, we can create objects of our Counter class in main, and access the static variable.
    
    ```python
    public class MyClass {
    	public static void main(String[] args) {
    		Counter c1 = new Counter();
    		Counter c2 = new Counter();
    		System.out.println(Counter.COUNT);
    	}
    }
    ```
    
    the output is 2, bc the COUNT variable is static and gets incremented by 1 each time a new object of the Counter class is created. In the code abv, we've created 2 objects.
    
    You can also access the static variable using any object of that class, such as c1.COUNT.
    
    note: it's a common practice to use upper case when naming a static variable, but not mandatory.
    
-   for methods
    
    the syntax for static methods are basically the same as for static variables.
    
    ```java
    public class Vehicle {
    	public static void horn() {
    		System.out.println("Beep");
    	}
    }
    ```
    
    now, the horn method can be called w/o creating an object:
    
    ```java
    public class MyClass {
    	public static void main(String[] args) {
    		Vehicle.horn();
    	}
    }
    ```
    
    another example of a static method are those of the Math class, which is why you can call them w/o creating a math object.
    
    note: also, the main method must always be static.
    
    ```java
    class Person {
    public static int pCount;	
    public static void main(String[ ] args) {			
       Person.pCount = 1; 
       Person.pCount++;
       System.out.println(Person.pCount);		
      }
    }
    //will output 2
    ```
    
-   static vs. non-static(instance)
    
    -   static invoked using class name, i.e. Dog.makeNoise()
    -   instance methods are invoked using an instance name, i.e. maya.makeNoise()
    -   static methods can't access "my" instance variables bc there is no "me"
    
    ```java
    //static
    public static void makeNoise() {
    	System.out.println("Bark!");
    }
    //this method can't access weightInPounds
    ```
    
    ```java
    //invocation
    Dog.makeNoise();
    ```
    
    ```java
    //non-static
    public void makeNoise() {
    	if (weightInPounds < 10) {
    		System.out.println("yipyipyip!");
    	} else if (weightInPounds < 30) {
    		System.out.println("bark. bark.");
    	} else { System.out.println("woof!"); }
    }
    ```
    
    ```java
    //invocation
    maya = newDog(100);
    maya.makeNoise();
    ```
    
    some classes are never instantiated. i.e., Math.
    
    -   x = Math.round(5.6);
    
    This is much nicer than:
    
    ```java
    Math m = new Math();
    x = m.round(x);
    ```
    
    sometimes, classes may have a mix of static and non-static methods, i.e.
    
    ```java
    public static Dog maxDog(Dog d1, Dog d2) {
    	if (d1.weightInPounds > d2.weightInPounds) {
    		return d1;
    	}
    	return d2;
    }
    //comparing the dogs: other file is using the non-static method abv(after Math class ex)
    //return type is dog: returns one w/ heavier weight
    ```
    
    can't call non-static method with class
    
    need to create instance of class to invoke non-static method(called public scope)
    
    -   need to create a new "variable" with the type of the class & instantiate with the new dog.
    -   Dog d = new Dog()
        -   Dog d = declare variable
        -   new Dog() = instantiate a new instance of the class
        -   \= is assign the instance to the variable
    
    ```java
    //can also do non-static class
    //impartial judge:
    public Dog maxDog(Dog d2) {
    	if (weightInPounds > d2.weightInPounds) {
    		return this;
    	}
    	return d2;
    }
    
    //using this & not using this has no difference, but in some situations, you have to use it. it is when the parameter has same name as variable, in order to differentiate between parameter and your own variable, have to use this
    
    //dogs judging themselves against other dogs:
    public Dog maxDog(Dog d2) {
    	if (this.weightInPounds > d2.weightInPounds) {
    		return this;
    	}
    	return d2;
    }
    //when comparing two dogs, we can use non-static method as well. can also use this, where you use non-static method, then compare yourself to another dog. use that one particular instance. will invoke this method from the instance.
    //specific dog has to do the judging
    ```
    
    ```java
    public class DogLauncher {
    	public static void main(String[] args) {
    		Dog d = new Dog(15);
    		
    		Dog d2 = new Dog(100);
    	
    		//Dog bigger = Dog.maxDog(d, d2);
    		Dog bigger = d.maxDog(d2);
    		// in this case, this dog does the judging to see if I am bigger & decides to know
    		bigger.makeNoise();
    
    		System.out.println(d.binomen);
    		//will be the same as
    		System.out.println(d2.binomen);
    	// if have static variable, you can access the variable using the instance, like d & d2(the variable of the instance). However, common practice is using the class to access the static variable instead, so:
    		System.out.println(Dog.binomen);
    	}
    }
    ```
    
    ```java
    public class Dog {
    	public int weightInPounds;
    	public static String binomen = "Canis familiaris";
    //all dogs have the same scientific name
    	
    	/** One integer constructor for dogs. */
    	public Dog(int w) {
    		weightInPounds = w;
    	}
    
    	public void makeNoise() {
    		if (weightInPounds < 10) {
    			System.out.println("yip!");
    		} else if (weightInPounds < 30) {
    			System.out.println("bark.");
    		} else {
    			System.out.println("wooof!");
    		}
    	}
    
    	public static Dog maxDog(Dog d1, Dog d2) {
    		if (d1.weightInPounds > d2.weightInPounds)
    			return d1;
    		}
    		return d2;
    	}
    
    	public Dog maxDog(Dog d2) {
    		if (weightInPounds > d2.weightInPounds) {
    			return this;
    		}
    		return d2;
    	}
    
    	public Dog maxDog(Dog d2) {
    		if (this.weightInPounds > d2.weightInPounds) {
    			return this;
    		}
    		return d2;
    	}
    ```
    
    a class may have a mix of static & non-static members.
    
    -   a variable or method defined in a class is also called a member of that clas.
    -   static members are accessed using class name, e.g. Dog.binomen
    -   Non-static members cannot be invoked using class name: ~~Dog.makeNoise()~~
        -   when have static keyword on the definition of method/variable, but not as a name.
    -   Static methods must access instance variables via a specific instance, e.g. d1
    
    when invoke static method/variable, use class name to call. for instance methods/variables, use instance(variable name of the class) to call the non-static methods/variables/attributes.
    
-   extra code
    
    ```java
    public class DogLauncher {
    	public static void main(String[] args) {
    		Dog smallDog; //Declaration of a dog variable
    		new Dog(20);//Instantiation of the Dog class as a Dog object
    		smallDog = new Dog(5); //instantiation & assignment
    		Dog hugeDog = new Dog(150); //declaration, instantiation and assignment
    		smallDog.makeNoise();
    		hugeDog.makeNoise();//invocation of the 150 pound Dog's makeNoise method
    	}
    }
    //dot notation means that we want to use a method or variable belonging to hugeDog, or more succinctly, a member of hugeDog
    ```
    
    ```java
    //every method/function is associated with some class
    //to run a class, we must define a main method
    //not all classes have main method
    public class Dog {
    	public static void makeNoise() {
    		System.out.println("Bark!");
    	}
    }
    ```
    
    ```java
    public class DogLauncher {
    	public static void main(String[] args) {
    		Dog.makeNoise();
    	}
    }
    ```
    
    ```java
    public class Dog {
    	public int weightInPounds;
    	// abv: instance variable. can have as many of these as you want.
    	
    	public Dog(int startingWeight) {
    		weightInPounds = startingWeight;
    	}
    	//abv: constructor. similar to method, but not. determines how to instantiate the class
    	
    	public void makeNoise() {
    		if (weightInPounds < 10) {
    			System.out.println("yipyipyip!");
    		} else if (weightInPounds < 30) {
    			System.out.println("bark. bark.");
    		} else {
    			System.out.println("woof!");
    		}
    	}
    	//non-static method aka instance method. idea: if the method is going to be invoked by an instance of the class, then it should be non-static. roughly speaking: if the method needs to use "my instance variables", the method must be non-static.
    }
    ```