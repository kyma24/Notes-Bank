declaring variables in JS uses keyword **var**

```jsx
var x = 10;
// equals sign is assignment operator
```

note: JS is case sensitive, so lastName & lastname are not the same!

outputting variables is pretty straightforward, like in Python & Java.

```jsx
var x = 100;
document.write(x);

//or

var X = 100;
console.log(x);

X = 42;
console.log(x);
```

note: every statement is separated w/ a semicolon, like in regular Java.

in JavaScript,

-   first character of variable name **must** be a letter, underscore(\_), or dollar sign($). Other characters can be letters, digits, underscores, or dollar signs.
-   first character of a variable consequently **can't** be a number
-   variable names **can't** include a mathematical/logical operator in the name. i.e. 2 x something or this + that
-   variable names can't contain spaces(obviously)
-   other special symbols are not allowed.

extra note: there are no hyphens in JavaScript, since they are reserved for subtractions