-   functions in ECMAScript 6
    
    Prior to ES6, a JS function was defined like this:
    
    ```jsx
    function add(x,y) {
    	var sum = x + y;
    	console.log(sum);
    }
    ```
    
    ES6 introduces a new syntax for writing functions. The same function from above can be written as:
    
    ```jsx
    const add = (x, y) => {
    	let sum = x + y;
    	console.log(sum);
    }
    ```
    
    the new syntax will be useful when user just needs a simple function with one argument.
    
    Can skip typing **function** and **return**, as well as some parentheses and braces.
    
    ```jsx
    //i.e.
    const greet = x => "Welcome" + x;
    ```
    
    the code abv defines a function named **greet** that has one argument and returns a message.
    
    if there are no parameters, an empty pair of parentheses should be used, as in
    
    ```jsx
    const x = () => alert("Hi");
    ```
    
    the syntax is very useful for inline functions. i.e. assume that have an array, and for each element of the array need to execute a function. Use the **forEach** method of the array to call a function for each element:
    
    ```jsx
    var arr = [2, 3, 7, 8];
    
    arr.forEach(function(el) {
    	console.log(el * 2);
    });
    ```
    
    however, in ES6, the code above can be rewritten as following:
    
    ```jsx
    const arr = [2, 3, 7, 8];
    
    arr.forEach(v => {
    	console.log(v * 2);
    });
    ```