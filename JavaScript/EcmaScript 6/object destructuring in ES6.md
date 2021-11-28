-   object destructuring in ES6
    
    similar to Array destructuring, **Object destructuring** unpacks properties into distinct variables.
    
    ```jsx
    //i.e.
    let obj = {h:100, s: true};
    let {h, s} = obj;
    
    console.log(h); // 100
    console.log(s); // true
    ```
    
    can assign without declaration, but will be some syntax requirements for that:
    
    ```jsx
    let a, b:
    ({a, b} = {a: 'Hello ', b: 'Jack'});
    
    console.log(a + b); // Hello Jack
    ```
    
    the **()** with a **semicolon(;)** at the end are **mandatory** when destructuring without a declaration. However, can also do it as follows where the **()** are not required:
    
    ```jsx
    let {a, b} = {a: 'Hello ', b: 'Jack'};
    console.log(a + b);
    ```
    
    can also assign the object to new variable names.
    
    ```jsx
    //i.e.
    var o = {h: 42, s: true};
    var {h: foo, s: bar} = o;
    
    //console.log(h); //Error
    console.log(foo); // 42
    ```
    
    finally you can assign **default values** to variables, in case the value unpacked from the object is undefined.
    
    ```jsx
    //i.e.
    var obj = {id: 42, name: "Jack"};
    
    let {id = 10, age = 20} = obj;
    
    console.log(id); // 42
    console.log(age); // 20
    ```
    
    ```jsx
    //i.e. this will output Error
    const obj = {one: 1, two: 2};
    let {one:first, two:second} = obj;
    console.log(one);
    ```