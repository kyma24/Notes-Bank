-   animations
    
    now that know how to select and change DOM elements, can create a simple animation.
    
    Create a simple HTML page with a **box** element that will be animated using JS.
    
    ```html
    <style>
    	#container {
    		width: 200px;
    		height: 200px;
    		background: green;
    		position: relative;
    	}
    	#box {
    		width: 50px;
    		height: 50px;
    		background: red;
    		position: absolute;
    	}
    </style>
    <div id="container">
    	<div id="box"></div>
    </div>
    ```
    
    the **box** element is inside a container element. Note the position attribute used for the elements: the container is **relative** and the box is **absolute**. This will allow the user to create the animation relative to the container.
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f9ddffa9-3a94-4566-9acc-81098623a364/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T140343Z&X-Amz-Expires=86400&X-Amz-Signature=52a36b96e93140c9f8c93639b7648e9449b7e8fd3242a435322929ac9355bac8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    will be animating the red box to make it move to the right side of the container.
    
    to create an animation, need to change the properties of an element at small intervals of time. Can achieve this by using the **setInterval**() method, which allows to create a timer and call a function to change properties repeatedly at defined intervals(in milliseconds).
    
    ```jsx
    //i.e.
    var t = setInterval(move, 500);
    ```
    
    the code creates a timer that calls a **move**() function every 500 milliseconds. Now need to define the **move**() function, that changes the position of the box.
    
    ```jsx
    //starting position
    var pos = 0;
    //the box element
    var box = document.getElementById("box");
    
    function move() {
    	pos += 1;
    	box.style.left = pos+"px"; //px = pixels
    }
    ```
    
    the **move**() function increments the **left** property of the box element by one each time it is called.
    
    the following code defines a timer that calls the **move**() function every 10 milliseconds:
    
    ```jsx
    var t = setInterval(move, 10);
    ```
    
    however, this makes the box move to the right forever. To stop the animation when the box reaches the end of the container, add a simple check to the move() function and use the **clearInterval**() method to stop the timer.
    
    ```jsx
    function move() {
    	if(pos >= 150) {
    		clearInterval(t);
    	}
    	else {
    		pos += 1;
    		box.style.left = pos+"px";
    	}
    }
    ```
    
    when the left attribute of the box reaches the value of 150, the box reaches the end of the container, based on a container width of 200 and a box width of 50.
    
    ```jsx
    //final code:
    
    var pos = 0;
    //the box element
    var box = document.getElementById("box");
    var t = setInterval(move, 10);
    
    function move() {
    	if(pos >= 150) {
    		clearInterval(t);
    	}
    	else {
    		pos += 1;
    		box.style.left = pos+"px";
    	}
    }
    ```