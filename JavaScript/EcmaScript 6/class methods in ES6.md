-   class methods in ES6
    
    ES6 introduced a shorthand that doesn't require the keyword **function** for a function assigned to a method's name. One type of class method is the **prototype method**, which is available to objects of the class.
    
    ```jsx
    //i.e.
    class Rectangle {
    	constructor(height, width) {
    		this.height = height;
    		this.width = width;
    	}
    	get area() {
    		return this.calcArea();
    	}
    	calcArea() {
    		return this.height * this.width;
    	}
    }
    const square = new Rectangle(5, 5);
    console.log(square.area); // 25
    ```
    
    in the code above, **area** is a getter, **calcArea** is a method.
    
    Another type of method is the **static method**, which can't be called through a class instance. Static methods are often used to create utility functions for an application.
    
    ```jsx
    //i.e.
    class Point {
    	constructor(x, y) {
    		this.x = x;
    		this.y = y;
    	}
    	static distance(a, b) {
    		const dx = a.x - b.x;
    		const dy = a.y - b.y;
    		return Math.hypot(dx, dy);
    	}
    }
    const p1 = new Point(7, 2);
    const p2 = new Point(3, 8);
    
    console.log(Point.distance(p1, p2));
    ```
    
    as seen, the static **distance** method is called directly using the class name, w/o an object.