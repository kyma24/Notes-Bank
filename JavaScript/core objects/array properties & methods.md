-   length property
    
    JS arrays have useful **built-in** properties and methods(like Java and Python, again)
    
    an array's **length** property returns the number of its elements.
    
    ```jsx
    var courses = ["HTML", "CSS", "JS"];
    document.write(courses.length);
    ```
    
    the length property is always one more than the highest array index.
    
    if the array is empty, the length property returns 0.
    
-   combining arrays
    
    JS's **concat()** method allows to join arrays and create an entirely new array.
    
    also useable for other data types.
    
    ```jsx
    //i.e.
    var c1 = ["HTML", "CSS"];
    var c2 = ["JS", "C++"];
    var courses = c1.concat(c2);
    ```
    
    the resulting courses array contains 4 elements(HTML, CSS, JS, C++)
    
    note: the **concat** operation doesn't affect the _c1_ and _c2_ arrays - it returns the resulting concatenation as a new array.
    
-   associative arrays
    
    while many programming languages support arrays with named indexes(text instead of numbers), called **associative arrays** JS doesn't.
    
    However, can still used the named array syntax, which will produce an object.
    
    ```jsx
    var person = []; //empty array
    person["name"] = "John";
    person["age"] = 46;
    document.write(person["age"]);
    ```
    
    now, person is treated as an object, instead of being an array.
    
    the named indexes "name" and "age" become properties of the person object.
    
    as the person array is treated as an object, the standard array methods and properties will produce incorrect results. For example, **person.length** will return 0.
    
    it is better to use an **object** when want the index to be a string.
    
    use an array when you want the index to be a number, so it's easier to iterate through w/ for loop.