refer to an array element by referring to the index number written in square brackets(like Java _and_ Python)

this statement accesses the value of the first element in **courses** and changes the value of the second element.

```jsx
var courses = new Array("HTML", "CSS", "JS");
var course = courses[0]; // HTML
courses[1] = "C++"; //changes second element
```

attempting to access an index outside of the array returns the value **undefined**.

```jsx
var courses = new Array("HTML", "CSS", "JS");
document.write(courses[10]);
```