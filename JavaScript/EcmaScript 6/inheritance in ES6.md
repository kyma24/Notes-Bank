-   inheritance in ES6
    
    the **extends** keyword is used in class declarations or class expressions to create a child of a class. The child inherits the properties and methods of the parent.
    
    ```jsx
    //i.e.
    class Animal {
    	constructor(name) {
    		this.name = name;
    	}
    	speak() {
    		console.log(this.name + ' makes a noise.');
    	}
    }
    class Dog extends Animal {
    	speak() {
    		console.log(this.name + ' barks.');
    	}
    }
    
    let dog = new Dog('Rex');
    dog.speak();
    ```
    
    in above code, the **Dog** class is a child of the **Animal** class, inheriting its properties and methods.
    
    note that if there's a constructor present in the subclass, it needs to first call **super**() before using **this**. Also, the **super** keyword is used to call parent's methods.
	
	i.e., can modify the program above to the following:
	```jsx
	class Animal {
		constructor(name){
			this.name = name;
		}
		speak(){
			console.log(this.name + ' makes a noise.');
		}
	}
	
	class Dog extends Animal {
		speak() {
			super.speak(); // Super
			console.log(this.name + ' barks.');
		}
	}
	
	let dog = new Dog('Rex');
	dog.speak();
	```
	
	note: in the code abv, the parent's **speak()** method is called using the **super** keyword.