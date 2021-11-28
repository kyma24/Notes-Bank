-   follow the mouse
    
    -   basic approach
        
        first, we need to draw something: a circle in this case.
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ce1905e4-9cdd-44e3-96ee-3fb163f0b00a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T153517Z&X-Amz-Expires=86400&X-Amz-Signature=ebda253a84901932d9b0938355018402aab9720fd8f167e99284c24bd06b6a10&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        second, the circle isn't going to be planted in a single location inside the canvas. The position will change based on where exactly the mouse cursor is at any given time. This means that we need to redraw the circle each time the mouse position changes:
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e300ba11-82db-4d67-a1a4-f5209734a4a1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T153556Z&X-Amz-Expires=86400&X-Amz-Signature=785d4373dc8538c84e2efc2fa02eba5bd4e5d90cfa77a0670648a2101e523654&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        by putting these 2 things together, the objective is reached. Now, that means that the concepts aren't that hard to wrap your head around. Some things that you may not have realized are relevant in the example.
        
    -   getting started
        
        first need HTML page with canvas element ready to run.
        
        ```html
        <!DOCTYPE html>
        <html>
         
        <head>
          <title>Canvas Follow Mouse</title>
          <style>
            canvas {
              border: #333 10px solid;
            }
         
            body {
              padding: 50px;
            }
          </style>
        </head>
         
        <body>
          <canvas id="myCanvas" width="550px" height="350px"></canvas>
         
          <script>
            var canvas = document.querySelector("#myCanvas");
            var context = canvas.getContext("2d");
             
          </script>
         
        </body>
         
        </html>
        ```
        
        at this moment, there isn't much going on here. There's a canvas element, and the element has id value of myCanvas. As a timesaver, there will be 2 lines of code provided that are needed to access the canvas element & its rendering context.
        
    -   drawing the circle
        
        the first thing to do is draw the circle. Inside script tag, add the following code after the line w/ the context variable:
        
        ```jsx
        function update() {
          context.beginPath();
          context.arc(100, 100, 50, 0, 2 * Math.PI, true);
          context.fillStyle = "#FF6A6A";
          context.fill();
        }
        update();
        ```
        
        all that's being done here is defining a function called update that contains code for drawing the circle. Note that we don't only define the update function, we also invoke it as well right afterwards. This means that if the page is tested in a browser, something like this will be seen:
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bc0366d2-8b40-407a-ba76-ebc664104946/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T153620Z&X-Amz-Expires=86400&X-Amz-Signature=3416945256b4e8176698acb566c53d26e43b1f8cdd186131a79242df9d3c7e20&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        the circle has radius of 50 pixels & positioned at the (100, 100) mark. For now, the position of the circle will be kept fixed. That won't last long after the mouse position is obtained.
        
    -   getting the mouse position
        
        -   listening for mouse event
            
            let's look at the code for the first part.
            
            go ahead and add following code just above the update function:
            
            ```jsx
            var mouseX = 0;
            var mouseY = 0;
            
            canvas.addEventListener("mousemove", setMousePosition, false);
            
            function setMousePosition(e) {
            	mouseX = e.clientX;
            	mouseY = e.clientY;
            }
            ```
            
            what the code does is pretty straightforward. we are listening for the mousemove event on the canvas element, and when that event is overheard, we call the setMousePosition event handler function thing:
            
            ```jsx
            function setMousePosition(e) {
            	mouseX = e.clientX;
            	mouseY = e.clientY;
            }
            ```
            
            all the setMousePosition function does is assign the current horizontal & vertical mouse position to the mouseX and mouseY properties. It does that by relying on the clientX and clientY properties that the MouseEvent-based event argument object provides.
            
        -   getting exact mouse position
            
            the mouse position stored by the mouseX and mouseY properties currently only store the position from the top-left corner of the browser window. They don't take into account where the canvas element is located on the page, so the mouse position values we have right now are going to be inaccurate, which isn't good.
            
            to fix this, we have the getPosition function that was seen earlier:
            
            ```jsx
            function getPosition(el) {
            	var xPosition = 0;
            	var yPosition = 0;
            
            	while (el) {
            		xPosition += (el.offsetLeft - el.scrollLeft + el.clientLeft);
            		yPosition += (el.offsetTop - el.scrollTop + el.clientTop);
            		el = el.offsetParent;
            	}
            	return {
            		x: xPosition,
            		y: yPosition
            	};
            }
            ```
            
            add this function towards the bottom of the code below the update function. You can put this function toward the top if wanted, but it's generally preferred to have helper functions towards the bottom of the code & out of sight.
            
            anyway, the way this function is used is by passing in the element whose position you are interested in. This function then returns an object containing the x and y position of the element. We'll use this function to figure out where our canvas element is on the page and then adjust our mouseX and mouseY values accordingly.
            
            To get the getPosition function & fix the mouseX and mouseY values, make the following additions and modifications that are bolded/highlighted:
            
            ```jsx
            **var canvasPos = getPosition(canvas);**
            var mouseX = 0;
            var mouseY = 0;
            
            canvas.addEventListener("mousemove", setMousePosition, false);
            
            function setMousePosition(e) {
            	**mouseX = e.clientX - canvasPos.x;
            	mouseY = e.clientY - canvasPos.y;**
            }
            ```
            
            the canvasPos variable now stores the position returned by the getPosition function. In the setMousePosition event handler, we use the returned x and y values from canvasPos to adjust the value stored by the mouseX and mouseY variables.
            
    -   moving the circle
        
        in getting the mouse position, we got the mouse code all setup with the mouseX and mouseY variables storing the mouse's current position inside the canvas. All that remains is to hook the values up with the drawing code inside the update function to have the circle's position reflect the mouse position.
        
        First, we are going to turn our boring update function into the target of a requestAnimationFrame callback. This will ensure this function gets synced up w/ our browser's drawing rate(~60 times per sec). This is a very simple mod. Go ahead and add the following bolded/highlighted line towards the bottom of the update function:
        
        ```jsx
        function update() {
        	context.beginPath();
        	context.arc(100, 100, 50, 0, 2 * Math.PI, true);
        	context.fillStyle = "#FF6A6A";
        	context.fill();
        
        	**requestAnimationFrame(update);**
        }
        update();
        ```
        
        next we need to update our circle drawing code to use the mouseX and mouseY values instead of using the fixed (100, 100) position that we specified initially. Make the following highlighted/bolded change to the context.arc() call:
        
        ```jsx
        function update() {
        	context.beginPath()
        	context.arc(**mouseX, mouseY**, 50, 0, 2 * Math.PI, true);
        	context.fillStyle = "#FF6A6A";
        	context.fill();
        
        	requestAnimationFrame(update);
        }
        update();
        ```
        
        once the change has been made, save the HTML doc and preview. When you move the mouse around the canvas, the circle will follow the cursor around, and this is what's going to happen:
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ea45135b-8abb-45db-a977-2f4a5803a0e0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T153648Z&X-Amz-Expires=86400&X-Amz-Signature=230d595571192ac5d324f6c0aef0468089dacd0cc8bf5fb73804de8f2cb9e3e5&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        the circle is following the mouse position, but the circle's earlier positions aren't being cleared out. The way to fix this is to clear out everything in the canvas before drawing our circle at its new position, and that is much simpler than it sounds.
        
        to make the fix, go ahead and add the following highlighted line of code towards the top of the update function:
        
        ```jsx
        function update() {
        	**context.clearRect(0, 0, canvas.width, canvas.height);**
        
        	context.beginPath();
        	context.arc(mouseX, mouseY, 50, 0, 2 * Math.PI, true);
        	context.fillStyle = "#FF6A6A";
        	context.fill();
        	
        	requestAnimationFrame(update);
        }
        ```
        
        the line added contains a call to the clearRect method, and this method is responsible for clearing all pixels from a canvas region. The way we use it is by passing in the dimensions of the region we want to clear, and what we do is pass in the full dimensions of our canvas to get everything cleared out:
        
        ```jsx
        context.clearRect(0, 0, canvas.width, canvas.height);
        ```
        
        this ensures that our circle is being drawn onto a blank surface w/ no traces of earlier draw operations remaining. If the page is previewed, the example should work perfectly.
        
    -   why use requestAnimationFrame?
        
        you may have noticed that all of the drawing-related code inside the update function is looped by the requestAnimationFrame function. There is no animation going on here. We are simply moving the mouse cursor around, and we want to update our circle's position only when the mouse circle positions. Given all of that, why wasn't all of the drawing code inside the mousemove event handler instead? that would look like this:
        
        ```jsx
        canvas.addEventListener("mousemove", setMousePosition, false);
        
        function setMousePosition(e) {
        	mouseX = e.clientX - canvasPos.x;
        	mouseY = e.clientY - canvasPos.y;
        
        	context.clearRect(0, 0, canvas.width, canvas.height);
        
        	context.beginPath();
        	context.arc(mouseX, mouseY, 50, 0, 2 * Math.PI, true);
        	content.fillStyle = "#FF6A6A";
        	context.fill();
        }
        ```
        
        if this change were to be made(and get rid of the update function completely), our example would sitll work. the example may work just as well as the requestAnimationFrame approach.
        
        The reason has to do with helping the browser not do unnecessary work and doing the "right" thing since our end goal is to draw something on the screen. When it comes to drawing things onto the screen, we want to be in-sync with when the browser is ready to paint the pixels. The mousemove event has no idea when the browser is ready to draw to the screen, so the event handler will unnecessarily try to force the browser to paint the screen. The only way to avoid this is what we did and use the requestAnimationFrame function.
        
        We separated code for updating the mouse position from the code for actually drawing on the screen. This ensures that we only draw our new circle when the browser is ready. When the circle is about to be drawn, we ensure that the mouse position at that time is as accurate as possible.
        
    -   final code
        
        ```html
        <!DOCTYPE html>
        <html>
         
        <head>
          <title>Canvas Follow Mouse</title>
          <style>
            canvas {
              border: #333 10px solid;
            }
         
            body {
              padding: 50px;
            }
          </style>
        </head>
         
        <body>
          <canvas id="myCanvas" width="550px" height="350px"></canvas>
         
          <script>
            var canvas = document.querySelector("#myCanvas");
            var context = canvas.getContext("2d");
            function update() {
        			context.clearRect(0, 0, canvas.width, canvas.height);
        
        		  context.beginPath();
        		  context.arc(mouseX, mouseY, 50, 0, 2 * Math.PI, true);
        		  context.fillStyle = "#FF6A6A";
        		  context.fill();
        
        			requestAnimationFrame(update);
        		}
        		update();
        		var canvasPos = getPosition(canvas);
        		var mouseX = 0;
        		var mouseY = 0;
         
        		canvas.addEventListener("mousemove", setMousePosition, false);
         
        		function setMousePosition(e) {
        		  //mouseX = e.clientX;
        			//mouseY = e.clientY;
        			mouseX = e.clientX - canvasPos.x;
        			mouseY = e.clientY - canvasPos.y;
        		}
        		update();
        		function getPosition(el) {
        		  var xPosition = 0;
        		  var yPosition = 0;
         
        		  while (el) {
        		    xPosition += (el.offsetLeft - el.scrollLeft + el.clientLeft);
        		    yPosition += (el.offsetTop - el.scrollTop + el.clientTop);
        		    el = el.offsetParent;
        		  }
        		  return {
        		    x: xPosition,
        		    y: yPosition
        		  };
        		}
          </script>
         
        </body>
         
        </html>
        ```
        
    
    [see explanation here](https://www.kirupa.com/canvas/follow_mouse_cursor.htm)