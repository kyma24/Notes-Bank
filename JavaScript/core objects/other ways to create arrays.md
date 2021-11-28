can also declare an array, tell it the number of elements it will store, and add the elements later(like in Java & Python, w/ downsides)

```jsx
var courses = new Array(3);
courses[0] = "HTML";
courses[1] = "CSS";
courses[2] = "JS";
```

an array is a special type of object. it uses numbers to access its elements, and an object uses names to access its members.

JS arrays are dynamic, so it is possible to declare an array and not pass any arguments with the Array() constructor. Can then add the elements dynamically(though logically will have a high Big O notation)

```jsx
var courses = new Array();
courses[0] = "HTML";
courses[1] = "CSS";
courses[2] = "JS";
courses[3] = "C++";
```

**Array Literal**:

for greater simplicity, readability, and execution speed, can also declare arrays using the **array literal** syntax.

```jsx
var courses = ["HTML", "CSS", "JS"];
```

this results in the same array as the one created with the **new Array()** syntax.

can access & modify the elements of the array using the index number, as did before.

the **array literal** syntax is the recommended way to declare arrays.