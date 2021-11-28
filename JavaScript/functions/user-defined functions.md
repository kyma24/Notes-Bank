JS function is a block of code designed to perform a particular task.(Python function, Java & HTML/CSS classes) Main advantages:

-   code reuse: define the code once & use many times
-   use the same code many times w/ different arguments to produce different resuls.

JS functions are executed when "something" invokes(or calls) it.

-   defining a function
    
    to define a JS function, use the function keyword, followed by the name of the function, followed by a set of parentheses()
    
    code to be executed is placed inside curly brackets
    
    ```jsx
    function name() {
    	//code to be executed
    }
    ```
    
    note: function names can include letters, digits, underscores, dollar signs. (same rules as variables)
    
-   calling a function
    
    to execute a function, you need to call it.
    
    to call a function, start w/ the name of the function, then follow it w/ the argument in parentheses.
    
    ```jsx
    function myFunction() {
    	alert("Calling a Function!");
    }
    
    myFunction();
    ```
    
    note: remember the semicolon after the function calling
    
    once function is defined, JS allows you to call as many times as you want to.
    
    ```jsx
    function myFunction() {
    	alert("Alert box!");
    }
    
    myFunction();
    //"Alert box!"
    
    //some other code
    
    myFunction();
    //"Alert box!"
    ```
    
    note: you can also call a function using syntax myFunction.call(). The difference is that when calling this way, you're passing the 'this' keyword to a function.