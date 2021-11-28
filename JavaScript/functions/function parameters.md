functions can take parameters

function parameters are the names listed in the function's definition.

```jsx
//SYNTAX
functionName(param1, param2, param3) {
	//some code
}
```

as w/ variables, parameters should be given names, which are separated by commas within parentheses.

-   using parameters
    
    after defining the parameters, you can use them inside function:
    
    ```jsx
    function sayHello(name) {
    	alert("Hi, " + name);
    }
    
    sayHello("David");
    ```
    
    this function takes one parameter which is called name. When calling the function, provide the parameter's value/argument inside the parentheses.
    
    note: function arguments are the real values passed to & received by the function, not the variables.
    

you can define a single function, and pass different parameter values/arguments to it.

```jsx
function sayHello(name) {
	alert("Hi, " + name);
}
sayHello("David");
sayHello("Sarah");
sayHello("John");
```

note: this will execute the function's code each time for the provided argument