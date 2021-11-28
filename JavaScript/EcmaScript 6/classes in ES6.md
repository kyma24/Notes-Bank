-   classes in ES6
    
    how to create a **class** that can be used to create multiple objects of the same structure.
    
    a class uses the keyword **class**(like Python) and contains a **constructor** method for initializing(again, like Python & Java).
    
    ```jsx
    //i.e.
    class Rectangle {
    	constructor(height, width) {
    		this.height = height;
    		this.width = width;
    	}
    }
    ```
    
    a declared class can then be used to create multiple objects using the keyword **new**.
    
    ```jsx
    //i.e.
    const square = new Rectangle(5, 5);
    const poster = new Rectangle(2, 3);
    ```
    
    note that class declarations are **not hoisted** while function declarations are.
    
    if try to access class before declaring it, **ReferenceError** will be returned.
    
    can also define a class w/ a **class expression**, where the class can be named or unnamed.
    
    a **named** class looks like:
    
    ```jsx
    var Square = class Rectangle {
    	constructor(height, width) {
    		this.height = height;
    		this.width = width;
    	}
    };
    ```
    
    in the unnamed class expression, a variable is simply assigned the class definition:
    
    ```jsx
    var Square = class {
    	constructor(height, width) {
    		this.height = height;
    		this.width = width;
    	}
    }
    ```
    
    the **constructor** is a special method which is used for creating and initializing an object created with a class.
    
    there can only be **one** constructor in each class(ofc).