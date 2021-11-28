-   const
    
    **const** variables have the same scope variables declared using **let**. The difference is that const variables are **immutable** - they aren't allowed to be reassigned(much like Java's final)
    
    i.e. the following generates an exception:
    
    ```jsx
    const a = 'Hello';
    a = 'Bye';
    ```
    
    note that **const** is not subject to **Variable Hoisting** too, which means that **const** declarations don't move to the top of the current execution context.
    
    Also note that ES6 code will run only in browsers that support it. Older devices and browsers that don't support this will return a syntax error.