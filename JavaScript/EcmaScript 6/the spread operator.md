-   the spread operator
    
    this operator is similar to the Rest Parameter, but it has another purpose when used in objects or arrays of function calls(arguments).
    
    ### Spread in function calls
    
    it is common to pass the elements of an array as arguments to a function.
    
    Before ES6, used the following method:
    
    ```jsx
    function myFunction(w, x, y, z) {
    	console.log(w + x + y + z);
    }
    var args = [1, 2, 3];
    myFunction.apply(null, args.concat(4));
    ```
    
    ES6 provides an easy way to do the example above with **spread operators**
    
    ```jsx
    const myFunction = (w, x, y, z) => {
    	console.log(w + x + y + z);
    };
    let args = [1, 2, 3];
    myFunction(...args, 4);
    ```
    
    ```jsx
    //i.e.
    var dateFields = [1970, 0, 1]; // 1 Jan 1970
    var date = new Date(...dateFields);
    console.log(date);
    ```
    
    ### Spread in array literals
    
    before ES6, used the following syntax to add an item at middle of an array:
    
    ```jsx
    var arr = ["One", "Two", "Five"];
    
    arr.splice(2, 0, "Three");
    arr.splice(3, 0, "Four");
    console.log(arr);
    ```
    
    can use methods such as push, splice, and concat, for example, to achieve this in different positions of the array. However, in ES6 the spread operator lets the user do this more easily:
    
    ```jsx
    let newArr = ['Three', 'Four'];
    let arr = ['One', 'Two', ...newArr, 'Five'];
    console.log(arr);
    ```
    
    ### Spread in object literals
    
    in objects it copies the own enumerable properties from the provided object onto a new object.
    
    ```jsx
    const obj1 = {foo: 'bar', x: 42};
    const obj2 = {foo: 'bax', y: 5};
    
    const clonedObj = {...obj1}; // {foo: "bar", x: 42}
    const mergedObj = {...obj1, ...obj2}; // {foo: "baz", x: 42, y: 5}
    ```
    
    however, if try to merge them won't get expected result:
    
    ```jsx
    const obj1 = {foo: 'bar', x: 42};
    const obj2 = {foo: 'baz', y: 5};
    const merge = (...objects) => ({..objects});
    
    let mergedObj = merge(obj1, obj2);
    // {0: {foo: 'bar', x: 42}, 1: {foo: 'baz', y: 5} }
    
    let mergedObj2 = merge({}, obj1, obj2);
    // {0: {}, 1: {foo: 'bar', x: 42}, 2: {foo: 'baz', y: 5} }
    ```
    
    note that shallow cloning or merging objects is possible with another operator called **Object.assign()**.
    
    ```jsx
    //i.e. output is 4
    let nums = [3, 4, 5];
    let all = [1, 2, ...nums, 6];
    console.log(all[3]);
    ```