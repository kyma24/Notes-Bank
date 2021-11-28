spaces and line breaks aren't important. An object definition can span multiple lines.

```jsx
var John = {
	name: "John",
	age: 25
};
var James = {
	name: "James",
	age: 21
};
```

no matter how the object is created, the syntax for accessing the properties and methods don't change.

```jsx
document.write(John.age);
```

There is a second accessing syntax that should be remembered: John\['age'\]