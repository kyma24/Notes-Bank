-   loops in ECMAScript 6
    
    in JS we commonly use the **for** loop to iterate over values in a list:
    
    ```jsx
    let arr = [1, 2, 3];
    for (let k = 0; k < arr.length; k++) {
    	console.log(arr[k]);
    }
    ```
    
    the **for...in** loop is intended for iterating over the enumerable keys of an object.
    
    ```jsx
    //i.e.
    let obj = {a: 1, b: 2, c: 3};
    for (let v in obj) {
    	console.log(v);
    }
    ```
    
    note that the **for...in** loop should **not** be used to iterate over arrays bc, depending on the JS engine, it could iterate in an arbitrary order. Also, the iterating variable is a **string**, not a number, so if try to do any math with the variable, will be performing string concatenation instead of addition.
    
    ES6 introduces the new **for...of** loop, which creates a loop iterating over iterable objects.
    
    ```jsx
    //i.e.
    let list = ["x", "y", "z"];
    for (let val of list) {
    	console.log(val);
    }
    ```
    
    during each iteration the **val** variable is assigned the corresponding element in the list.
    
    The **for...of** loop works for other iterable objects as well, including **strings**.
    
    ```jsx
    for (let ch of "Hello") {
    	console.log(ch);
    }
    ```
    
    the **for...of** loop also works on the newly introduced collections (**Map**, **Set**, **WeakMap**, and **WeakSet**). Note that ES6 code will run only in browsers that support it. Older devices and browsers that don't support ES6 will return a syntax error.