ES6 also introduced new built-in methods to make several tasks easier. here will cover the most common ones.

### Array Element Finding
The legacy way to find the first element of an array by its value and a rule was the folowing:
```jsx
[4, 5, 1, 8, 2, 0].filter(function(x) {
	return x > 3;
})[0];
```

the new syntax is cleaner and more robust:
```jsx
[4, 5, 1, 8, 2, 0].find(x => x > 3);
```

can also get the index of the item above by using the **findIndex()** method:
```jsx
[4, 5, 1, 8, 2, 0].findIndex(x => x > 3);
```

### Repeating Strings
Before ES6 the following syntax was the correct way to repeat a string multiple times:
```jsx
console.log(Array(3 + 1).join("foo")); // foofoofoo
```

With new syntax, it becomes:
```jsx
console.log("foo".repeat(3)); // foofoofoo
```

### Searching Strings
Before ES6 only used the indexOf() method to find the position of the text in the string.
```jsx
//i.e.
"SoloLearn".indexOf("solo") === 0; // true
"SoloLearn".indexOf("Solo") === (4 - "Solo".length); // true
"SoloLearn".indexOf("loLe") !== -1; // true
"SoloLearn".indexOf("olo", 1) !== -1; // true
"SoloLearn".indexOf("olo", 2) !== -1; // false
```

ES6 has replaced this with a version that has cleaner and more simplified syntax:
```jsx
"SoloLearn".startsWith("Solo", 0); // true
"SoloLearn".endsWith("Solo", 4); // true
"SoloLearn".includes("loLe"); // true
"SoloLearn".includes("olo", 1); // true
"SoloLearn".includes("olo", 2); // false
```

it is always a good practice to refactor the code with the new syntax to learn new things and make the code more understandable.