-   ES6 objects
    
    JS variables can be **Object** data types that contain many values called **properties**.
    
    An object can also have properties that are function definitions called **methods** for performing actions on the object.(as in Java & Python...)
    
    ES6 introduces **shorthand** notations and **computed** property names that make declaring and using objects easier to understand.
    
    The new method definition shorthand doesn't require the colon(:) or **function** keyword, as in the **grow** function of the **tree** object declaration:
    
    ```jsx
    let tree = {
    	height: 10,
    	color: 'green',
    	grow() {
    		this.height += 2;
    		//like Java
    	}
    };
    tree.grow();
    console.log(tree.height); //12
    ```
    
    can also use a property value shorthand when initializing properties with a variable by the same name.
    
    i.e. properties **height** and **health** are being initialized with variables named **height** and **health**
    
    ```jsx
    let height = 5;
    let health = 100;
    
    let athlete = {
    	height,
    	health
    };
    ```
    
    when creating an object by using duplicate property names, the last property will overwrite the prior ones of the same name.
    
    i.e
    
    ```jsx
    var a = {x: 1, x: 2, x: 3, x: 4};
    ```
    
    note that duplicate property names generated a **SyntaxError** in ES5 when using strict mode. However, ES6 removed this limitation