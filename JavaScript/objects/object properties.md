you can access object properties in 2 ways.

```jsx
objectName.propertyName
//or
objectName['propertyName']
```

this example demonstrates how to access the age of the person object.

```jsx
var person = {
	name: "John", age: 31,
	favColor: "green", height: 183
);
var x = person.age;
var y - person['age'];
```

JS's built-in **length** property is used to count the number of characters in a property or string.

```jsx
var course = {name: "JS", lessons: 41};
document.write(course.name.length);
```

Objects are one of the core concepts in JS.