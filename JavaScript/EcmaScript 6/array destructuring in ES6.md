-   array destructuring in ES6
    
    the **destructuring** assignment syntax is a JS expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.
    
    ES6 has added a shorthand syntax for destructuring an array.
    
    Following example demonstrates how to unpack the elements of an array into distinct variables:
    
    ```jsx
    let arr = ['1', '2', '3'];
    let [one, two, three] = arr;
    
    console.log(one); // 1
    console.log(two); //2
    console.log(three); // 3
    ```
    
    can use also destructure an array returned by a function
    
    ```jsx
    //i.e.
    let a = () => {
    	return [1, 3, 2];
    };
    
    let [one, , two] = a();
    ```
    
    notice that left the second argument's place empty.
    
    the destructuring syntax also simplifies assignment and swapping values:
    
    ```jsx
    let a, b, c = 4, d = 8;
    [a, b = 6] = [2]; // a = 2, b = 6
    
    [c, d] = [d, c]; // c = 8, d = 4
    ```