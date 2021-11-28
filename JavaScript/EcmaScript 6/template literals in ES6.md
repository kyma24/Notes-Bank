-   template literals in ES6
    
    **Template literals** are a way to output variables in the string.
    
    prior to ES6 one has to break the string, for example:
    
    ```jsx
    let name = 'David';
    let msg = 'Welcome ' + name + '!';
    console.log(msg);
    ```
    
    ES6 introduces a new way of outputting variable values in strings. The same code above can be rewritten as:
    
    ```jsx
    let name = 'David';
    let msg = `Welcome ${name}!`;
    console.log(msg);
    ```
    
    notice that template literals are enclosed by the **backtick**(\`\`) character instead of double or single quotes.
    
    The **${expression}** is a placeholder, and can include any expression, which will get evaluated and inserted into the template literal.
    
    ```jsx
    //i.e.
    let a = 8;
    let b = 34;
    let msg = `The sum is ${a+b}`;
    console.log(msg);
    ```
    
    to escape a backtick in a template literal, put a backslash \\ before the backtick.