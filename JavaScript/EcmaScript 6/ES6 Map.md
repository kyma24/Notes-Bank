A **Map** object can be used to hold **key/value** pairs. A key or value in a map can be anything(objects and primitive values).
The syntax **new Map(\[iterable])** creates a Map object where **iterable** is an array or any other iterable object whose elements are arrays(with a key/value pair each).

An **Object** is similar to **Map** but there are importand differences that make usinga Map preferable in certain cases:
1. The keys can be any type including functions, objects, and any primitive.
2. You can get the size of a Map.
3. You can directly iterate over Map.
4. Performance of the Map is better in scenarios involving frequent addition and removal of key/value pairs.

The **size** property returns the number of key/value pairs in a map.
```jsx
//i.e.
let map = new Map([['k1', 'v1'], ['k2', 'v2']]);

console.log(map.size); // 2
```

#### Methods
**set(key, value** Adds a specified key/value pair to the map. If the specified key already exists, value corresponding to it is replaced with the specified value.
**get(key)** Gets the value corresponding to a specified key in the map. If the specified key doesn't exist, undefined is returned.
**has(key)** Returns true if a specified key exists in the map and false otherwise
**delete(key)** Deletes the key/value pair with a specified key from the map and returns true. Returns false if the element doesn't exist.
**clear()** Removes all key/value pairs from map
**keys()** Returns an Iterator of keys in the map for each element
**values()** Returns an Iterator of values in the map for each element
**entries** Returns an Iterator of array\[key, value] in the map for each element.

```jsx
//i.e.
let map = new Map();

map.set('k1', 'v1').set('k2', 'v2');

console.log(map.get('k1')); // v1

console.log(map.has('k2')); // true

for (let kv of map.entries())
	console.log(kv[0] + " : " + kv[1]);
```

the above example demonstrates some of the ES6 Map methods.

note that **Map** supports different data types i.e. 1 and "1" are two different keys/values.

```jsx
//output of this code is 1
const map = new Map(); map.set('one', 1); map.set('2', 'two');
if (map.has('two')) {
	console.log('two');
} else { console.log(map.get('one'));
}