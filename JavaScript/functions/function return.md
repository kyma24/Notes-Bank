function can have optional return statement. used to return a value from the function

statement is useful when making calculations that require a result.

when JS reaches a return statement, function stops executing(like break)

```jsx
function myFunction(a, b) {
	return a * b;
}

var x = myFunction(5, 6);
//Return value will end up in x
```

^if do not return anything from a function, it will return undefined

```jsx
function addNumbers(a, b) {
	var c = a + b;
	return c;
}
document.write(addNumbers(40, 2));
```