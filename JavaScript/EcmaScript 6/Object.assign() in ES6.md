-   Object.assign() in ES6
    
    ES6 adds a new **Object** method **assign()** that allows the user to combine multiple sources into one target to create a single new object.
    
    **Object.assign()** is also useful for creating a duplicate of an existing object.
    
    look at the following example to see how to combine objects:
    
    ```jsx
    let person = {
    	name: 'Jack',
    	age: 18,
    	sex: 'male'
    };
    
    let student = {
    	name: 'Bob',
    	age: 20,
    	xp: '2'
    };
    
    let newStudent = Object.assign({}, person, student);
    ```
    
    used **Object.assign()** where the first parameter is the **target object** want to apply new properties to.
    
    Every parameter after the first will be used as **sources** for the target. There are no limitations on the number of source parameters. However, order is important bc properties in the second parameter will be overridden by properties of the same name in third parameter, and so on.
    
    in example above, used a new object **{}** as the target and used two objects as sources.
    
    now, see how can use **assign()** to use a duplicate object w/o creating a reference(mutating) to the base object.
    
    in following example, assignment was used to try to generate a new object. However, using = creates a reference to the base object. Bc of this reference, changes intended for a new object mutate the original object:
    
    ```jsx
    let person = {
    	name: 'Jack',
    	age: 18
    };
    
    let newPerson = person; // newPerson references person
    newPerson.name = 'Bob';
    
    console.log(person.name); // Bob
    console.log(newPerson.name); // Bob
    ```
    
    to avoid this(mutations), use **Object.assign()** to create a new object.
    
    ```jsx
    //i.e.
    let person = {
    	name: 'Jack',
    	age: 18
    };
    
    let newPerson = Object.assign({}, person);
    newPerson.name = 'Bob';
    
    console.log(person.name); // Jack
    console.log(newPerson.name); // Bob
    ```
    
    finally, can assign a value to an object property in the **Object.assign()** statement.
    
    ```jsx
    //i.e.
    let person = {
    	name: 'Jack',
    	age: 18
    };
    
    let newPerson = Object.assign({}, person, {name: 'Bob'});
    ```
    
    ```jsx
    //i.e. this outputs 46
    const obj1 = {
      a: 0,
      b: 2,
      c: 4
    };
    const obj2 = Object.assign({c: 5, d: 6}, obj1);
    console.log(obj2.c, obj2.d);
    ```