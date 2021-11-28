-   default parameters in ES6
    
    in ES6, can put the default values right in the signature of the functions.
    
    ```jsx
    //i.e.
    function test(a, b = 3, c = 42) {
    	return a + b + c;
    }
    console.log(test(5)); //50
    ```
    
    example of an arrow function w/ default parameters:
    
    ```jsx
    const test = (a, b = 3, c = 42) => {
    	return a + b + c
    }
    console.log(test(5)); //50
    ```
    
    default value expressions are evaluated at function call time from left to right. This also means that default expressions can use the values of previously-filled parameters.