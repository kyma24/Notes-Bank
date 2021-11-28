-   methods
    
    methods are functions that are stored as object properties.
    
    the following syntax is used to create an object method:
    
    ```jsx
    methodName = function() {code lines}
    ```
    
    access an object method using the following syntax:
    
    ```jsx
    objectName.methodName()
    ```
    
    a method is a function, belonging to an object. It can be referenced using the **this** keyword.
    
    The **this** keyword is used as a reference to the current object, meaning that the objects properties and methods can be accessed using it.
    
    Defining methods is done inside the constructor function.
    
    ```jsx
    function person(name, age) {
    	this.name = name;
    	this.age = age;
    	this.changeName = function (name) {
    		this.name = name;
    	}
    }
    
    var p = new person("David", 21);
    p.changeName("John");
    //Now p.name equals to "John"
    ```
    
    in the above example, a method named **changeName** has been defined for the person, which is a function, that takes a parameter **name** and assigns it to the **name** property of the object.
    
    **this.name** refers to the name property of the object.
    
    the **changeName** method changes the object's **name** property to its argument.
    
-   method defining
    
    can also define the function outside of the constructor function and associate it with the object.
    
    ```jsx
    function person(name, age) {
    	this.name = name;
    	this.age = age;
    	this.yearOfBirth = bornYear;
    }
    function bornYear() {
    	return 2016 - this.age;
    }
    ```
    
    as seen, have assigned the object's **yearOfBirth** property to the **bornYear** function
    
    The **this** keyword is used to access the _age_ property of the object, which is going to call the method.
    
    note that it isn't necessary to write the function's parentheses when assigning it to an object.
    
-   calling example
    
    ```jsx
    function person(name, age) {
    	this.name = name;
    	this.age = age;
    	this.yearOfBirth = bornYear;
    }
    function bornYear() {
    	return 2016 - this.age;
    }
    
    var p = new person("A", 22);
    document.write(p.yearOfBirth());
    ```
    
    call the method by the **property name** specified in the constructor function, rather than the function name.