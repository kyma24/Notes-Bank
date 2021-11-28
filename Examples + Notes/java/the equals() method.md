-   comparing objects
    
    remember that when objects that are created, the variables store references to the objects.
    
    So, when objects are compared using the equality testing operator( == ), it actually compares the references and not the object values.
    
    ```java
    class Animal {
    	String name;
    	Animal(String n) {
    		name = n;
    	}
    }
    
    class MyClass {
    	public static void main(String[] args) {
    		Animal a1 = new Animal("Robby");
    		Animal a2 = new Animal("Robby");
    		System.out.println(a1 == a2);
    	}
    }
    ```
    
    despite having two objects with the same name, the equality testing returns false, because there are two different objects(two different references or memory locations).
    
    ```java
    class A {
     private int x;	
     public static void main(String[ ] args) {
       A a = new A();
       a.x = 5;
       A b = new A();
       b.x = 5;
       System.out.println(a == b);			
     }
    }
    
    //output is false bc it isn't referencing value. They both equal five, but they're two different objects. What the Boolean theory(==) is asking us is if they're both getting their reference from the same place.
    ```
    
-   equals()
    
    each object has a predefined equals() method that is used for semantical equality testing.
    
    But, to make it work for the classes, need to override it and check the conditions needed.
    
    There is a simple and fast way of generating the equals() method, other than writing it manually.
    
    Just right click in your class, go to Source → Generate hashCode() and equals()...
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5c3cd96f-7ee8-4bac-8565-2bc3fa5a540a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5c3cd96f-7ee8-4bac-8565-2bc3fa5a540a/Untitled.png)
    
    this will automatically create the necessary methods.
    
    ```java
    class Animal {
    	String name;
    	Animal(String n) {
    		name = n;
    	}
    	@Override
    	public int hashCode() {
    		final int prime = 31;
    		int result = 1;
    		result = prime * result + ((name == null) ? 0: name.hashCode());
    		return result;
    	}
    	@Override
    	public boolean equals(Object obj) {
    		if (this == obj)
    			return true;
    		if (obj == null)
    			return false;
    		if (getClass() != obj.getClass())
    			return false;
    		Animal other = (Animal) obj;
    		if (name == null) {
    			if (other.name != null)
    				return false;
    		} else if (!name.equals(other.name))
    			return false;
    		return true;
    	}
    }
    ```
    
    the automatically generated hashCode() method is used to determine where to store the object internally. Whenever equals is implemented, MUST allow to implement hashCode.
    
    Can run the test again, using the equals method:
    
    ```java
    public static void main(String[] args) {
    	Animal a1 = new Animal("Robby");
    	Animal a2 = new Animal("Robby");
    	System.out.println(a1.equals(a2));
    }
    ```
    
    can use the same menu to generate other useful methods, such as getters and setters for the class attributes.