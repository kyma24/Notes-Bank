-   var & let
    
    in ES6 have three ways of declaring variables:
    
    ```jsx
    var a = 10;
    const b = 'hello';
    let c = true;
    ```
    
    the type of declaration used depends on the necessary **scope**. **Scope** is the fundamental concept in all programming languages that defines the visibility of a variable.
    
    ### var & let
    
    unlike the **var** keyword, which defines a variable globally, or locally to an entire function regardless of block scope, **let** allows the user to declare variables that are limited in scope to the block, statement, or expression in which they are used.
    
    ```jsx
    //i.e.
    if (true) {
    	let name = 'Jack';
    }
    alert(name); //generates an error
    ```
    
    in this case, the **name** variable is accessible only in the scope of the **if** statement bc it was declared as **let**.
    
    To demonstrate the difference in scope between **var** and **let**, consider this example:
    
    ```jsx
    function varText() {
    	var x = 1;
    	if (true) {
    		var x = 2; //same variable
    		console.log(x); //2
    	}
    	console.log(x); //2
    }
    
    function letTest() {
    	let x = 1;
    	if (true) {
    		let x = 2; //different variable
    		console.log(x); //2
    	}
    	console.log(x); //1
    }
    ```
    
    one of the best uses for **let** is in loops:
    
    ```jsx
    for (let i = 0; i < 3; i++) {
    	document.write(i);
    }
    ```
    
    here, the **i** variable is accessible only within the scope of the **for** loop, where it is needed.
    
    note that **let** is not subject to **Variable Hoisting**, which means that **let** declarations don't move to the top of the current execution context