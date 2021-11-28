-   computed property names
    
    with ES6, can now use **computed property** names. Using the square bracket notation \[\], can use an expression for a property name, including concatenating strings. This can be useful in cases where want to create certain objects based on user data(e.g. id, email, and so on).
    
    ```jsx
    //ex 1
    let proper = 'name';
    let id = '1234';
    let mobile = '08923';
    
    let user = {
    	[prop]: 'Jack',
    	[`user_${id}`]: `${mobile}`
    };
    ```
    
    ```jsx
    //ex 2
    var i = 0;
    var a = {
    	['foo' + ++i]: i,
    	['foo' + ++i]: i,
    	['foo' + ++i]: i
    };
    ```
    
    ```jsx
    //ex 3
    var param = 'size';
    var config = {
    	[param]: 12,
    	['mobile' + param.charAt(0).toUpperCase() + param.slice(1)]: 4
    };
    console.log(config.mobileSize);
    ```
    
    it is very useful when need to create custom objects based on some variables.