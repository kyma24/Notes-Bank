can define multiple parameters for function by separating w/ commas.

```jsx
function myFunc(x, y) {
	//some code
}
```

example defines function myFunc to take 2 parameters

parameters are used within function's definition.

```jsx
function sayHello(name, age) {
	document.write(name + " is " + age + " years old.");
}
```

function parameters are names listed in function definition

when calling the function, provide the arguments in the same order in which you defined them

```jsx
function sayHello(name, age) {
	document.write(name + " is " + age + " years old.");
}

sayHello("John", 20);
```

if you pass more arguments than defined, they will be assigned to an array called arguments. Used like this: arguments\[0\], arguments\[1\], etc.

JS doesn't check the number of arguments received.

If a function is called w/ missing arguments(fewer than declared), the missing values are set to undefined, which indicates that it has not been assigned a value.