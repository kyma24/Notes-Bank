-   object constructor
    
    before, have created objects using the **object literal**(or initializer) syntax.
    
    ```jsx
    var person = {
    	name: "John", age: 42, favColor: "green"
    };
    ```
    
    this allows to create only a single object.
    
    Sometimes, need to set an "**object type**" that can be used to create a number of objects of a single type.
    
    The standard way to create an "object type" is to use an object **constructor function**.
    
    ```jsx
    function person(name, age, color) {
    	this.name = name;
    	this.age = age;
    	this.favColor = color;
    }
    
    //...just like Python's self
    ```
    
    the above function(person) is an object constructor(like the **init** function in Python), which takes parameters and assigns them to the object properties.
    
    note: The **this** keyword refers to the **current object**, much like **self** in Python.
    
    Note that **this** isn't a variable. It is a keyword, and its value can't be changed.
    
-   creating objects
    
    once have an object constructor, can use the **new** keyword to create new objects of the same type(like Java)
    
    ```jsx
    var p1 = new person("John", 42, "green");
    var p2 = new person("Amy", 21, "red");
    
    document.write(p1.age); //outputs 42
    document.write(p2.name); //outputs "Amy"
    ```
    
    _p1_ and _p2_ are now objects of the **person** type. Their properties are assigned to the corresponding values.
    
    ```jsx
    //i.e.
    function person (name, age) {
    	this.name = name;
    	this.age = age;
    }
    var John = new person("John", 25);
    var James = new person("James", 21);
    ```
    
    the object's properties can be accessed using the **dot syntax**.
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d36191fe-56b0-4314-b241-cef5e46f376c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T135154Z&X-Amz-Expires=86400&X-Amz-Signature=061c1837c599618f5cf53e6ae0d3226b7bd248b473a1e3187f77d57c6ab1ae5d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)