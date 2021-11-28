-   value types
    
    Value types are the basic types, and include byte, short, int, long, float, double, boolean, and char.
    
    **note:** String is an object; it is a list of characters :O
    
    data types store values in corresponding memory locations. **Thus, when you pass the variables into a method, you are basically operating on the value itself, not the variable.** ← does NOT change the value: may be useful
    
    ```java
    public class MyClass {
    	public static void main(String[ ] args) {
    		int x = 5;
    		addOneTo(x);
    		System.out.println(x);
    	}
    	static void addOneTo(int num) {
    		//void doesn't return anything; if we change it to return something, then the value x will be changed
    		num = num + 1;
    	}
    }
    ```
    
    The method from the example above takes the value of its parameter, which is why the original variable is not affected and 5 remains as its value.
    
-   reference types
    
    reference type stores address/reference to memory location where corresponding data is stored
    
    when creating object using constructor, a reference type is used
    
    ```java
    public class MyClass {
    	public static void main(String[] args) {
    		Person j;
    		j = new Person("John");
    		j.setAge(20);
    		celebrateBirthday(j);
    		System.out.println(j.getAge());
    }
    
    	static void celebrateBirthday(Person p) {
    		p.setAge(p.getAge() + 1);
    	}
    }
    ```
    
    **celebrateBirthday** takes Person object as parameter & increments its attribute.
    
    bc **j** = reference type, method affects object itself & is able to change actual value of its attribute.
    
    note: Arrays and Strings are also reference data types.