**Symbol.iterator** is the default iterator for an object. The for...of loops are based on this type of iterator.

In the example below, will see how should implement it and how **generator functions** are used.
```jsx
//i.e.
let myIterableObj = {
	[Symbol.iterator] : function* () {
		yield 1; yield 2; yield 3;
...
console.log([...myIterableObj]);
```
first, create an object, and use the **Symbol.iterator** and **generator function** to fill it with some values.

In the second line of the code, use a \* with the **function** keyword. It's called a **generator function(or gen function)**.

i.e. here is a simple case of how **gen functions** can be useful:
```jsx
function* idMaker() {
	let index = 0;
	while (index < 5)
		yield index++;
}
var gen = idMaker();
console.log(gen.next().value);
```
can exit and re-enter generator functions later. Their variable bindings(context) will be saved across re-entrances. They are a very powerful tool for asynchronous programming, especially when combined w/ Promises. They can also be useful for creating loops with special requirements.

Can nest **generator functions** inside each other to create more complex structures and pass the arguments while calling them. The example below will show a useful case of how can use **generator functions** and **Symbol.iterators** together.
```jsx
const arr = ['0', '1', '4', 'a', '9', 'c', '16'];
const my_obj = {
	[Symbol.iterator]: function*() {
		for(let index of arr) {
			yield `${index}`;
		}
	}
};
const all = [...my_obj]
	.map(i => parseInt(i, 10))
	.map(Math.sqrt)
	.filter((i) => i < 5)
	.reduce((i, d) => i + d);
console.log(all);
```
create an object of 7 elements by using **Symbol.iterator** and **generator functions**. In the second part, assign the object to a constant **all**. At the end, print its value.