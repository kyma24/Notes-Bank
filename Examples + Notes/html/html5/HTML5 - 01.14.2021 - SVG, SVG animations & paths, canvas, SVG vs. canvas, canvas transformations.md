-   SVG(Scalable Vector Graphics)
    
    1.  used to draw shapes w/ HTML-style markup
    2.  offers several methods for drawing paths, boxes, circles, text, and graphic images
    3.  isn't pixel based, so can zoom in infinitely w/o loss of quality
    
    -   svg image can be added into code using same as reg. image:
    
    ```html
    <img src="image.svg" alt="" height="300" />
    ```
    
    -   SVG defines vector-based graphics in XML format.
        
    -   drawing a circle:
        
        to draw shapes, first need to create SVG element tag:
        
        ```html
        <svg width="1000" height="1000"></svg>
        ```
        
        to create circle, add circle tag:
        
        ```html
        <svg width="2000" height="2000">
        	<circle cx="80" cy="80" r="50" fill="green" />
        	<!--like python turtle: include (x,y) and radius-->
        </svg>
        ```
        
        -   **cx**: pushes the center of the circle further to the right of the screen
        -   **cy**: pushes the center of the circle further down from the top of the screen
        -   **r**: defines the radius
        -   **fill**: determines the color of our circle
        -   **stroke**: adds an outline to the circle
        
        RESULT:
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/027c36d6-d80c-49da-8dce-2eb85447db13/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221209Z&X-Amz-Expires=86400&X-Amz-Signature=62670e5abc2470be8c2c12ed854f3a0abe4659a5bf511e50015ba605ecce4f32&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        -   note: every element and every attribute in SVG files can be animated
    -   other shape elements:
        
        **rect defines a rectangle:**
        
        ```html
        <svg width="2000" height="2000">
        	<rect width="300" height="100"
        	x="20" y="20" fill="green" />
        </svg>
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b9094b1f-9fc4-436a-82c9-0e201023d0ef/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221240Z&X-Amz-Expires=86400&X-Amz-Signature=278d7ffa210239d03940fc8cf7bb693df3184a9b4f07a07dba8f6885d2dc3201&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        The width and height attributes of the rect element define the height and the width of the rectangle.
        
        **line defines line segment:**
        
        ```html
        <svg width="400" height="410">
        	<line x1="10" y1="10" x2="200" y2="100"
        	style="stroke=#000000; stroke-linecap:round;
        	stroke-width:20" />
        </svg>
        ```
        
        (x1, y1) define the start coordinates(x2, y2) define the end coordinates.
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cde98cb3-2302-46c7-b2e3-a1b1712d0059/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221312Z&X-Amz-Expires=86400&X-Amz-Signature=f5a0a3b5ec521c495ea1b836584b0f5b8daa223a307de4d423cbee05beddad08&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        **polyline defines shapes built from multiple line definitions:**
        
        ```html
        <svg width="2000" height="500">
        	<polyline style="stroke-linejoin:miter; stroke:black;
        	stroke-width:12; fill: none;"
        	points="100 100, 150 150, 200 100" />
        </svg>
        ```
        
        Points are the polyline's coordinates.
        
        The code below will draw a black check sign:
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/75b40103-89b9-4e96-ab63-e9a664fa1968/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221333Z&X-Amz-Expires=86400&X-Amz-Signature=a10998c44175c4ac5dba82d991fad39dadc4a3dea184b156ada8d8f5e6727443&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
    -   ellipse and polygon:
        
        The **ellipse** is similar to the **circle**, with one exception:
        
        You can independently change the horizontal and vertical axes of its radius, using the **rx** and **ry** attributes.
        
        ```html
        <svg height="500" width="1000">
        	<ellipse cx="200" cy="100" rx="150" ry="70"
        	style="fill:green;" />
        </svg>
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fe5102ca-823d-41eb-b95b-5250016da479/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221410Z&X-Amz-Expires=86400&X-Amz-Signature=861aaf0e13b2e584dabe6a721fb31f027a0304a06458df77ed6ac74b5a0b2850&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        The **polygon** element is used to create a graphic with at least three sides. The polygon element is unique because it automatically closes off the shape for you.
        
        ```html
        <svg width="2000" height="2000">
        <polygon points="100 100, 200 200, 300 0"
        	style="fill:green; stroke:black;" />
        </svg>
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/33b6ed97-a0bb-4ea8-b182-9153642d1958/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221430Z&X-Amz-Expires=86400&X-Amz-Signature=4c8dd5d9b533d61f5abee2c08cb7a0a11838a31a6aa3007c9424da22e6e72825&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
-   SVG animations & paths
    
    SVG animations can be created using the animate element.
    
    The example below creates a rectangle that will change its position in 3 seconds and will then repeat the animation twice:
    
    ```html
    <svg width="1000" height="250">
    <rect width="150" height="150" fill="orange">
    	<animate attributeName="x" from="0" to="300"
    	dur="3s" fill="freeze" repeatCount="2" />
    </rect>
    </svg>
    ```
    
    **attributeName**: Specifies which attribute will be affected by the animation
    
    **from**: Specifies the starting value of the attribute
    
    **to**: Specifies the ending value of the attribute
    
    **dur**: Specifies how long the animation runs (duration)
    
    **fill**: Specifies whether or not the attribute's value should return to its initial value when the animation is finished (Values: "remove" resets the value; "freeze" keeps the “to value”)
    
    **repeatCount**: Specifies the repeat count of the animation
    
    In the example above, the rectangle changes its x attribute from 0 to 300 in 3 seconds.
    
    To repeat the animation indefinitely, use the value "indefinite" for the repeatCount attribute.
    
    The path element is used to define a path.
    
    The following commands are available for path data:
    
    **M**: moveto
    
    **L**: lineto
    
    **H**: horizontal lineto
    
    **V**: \*\*\*\*vertical lineto
    
    **C**: curveto
    
    **S**: smooth curveto
    
    **Q**: quadratic Bézier curve
    
    **T**: smooth quadratic Bézier curveto
    
    **A**: elliptical Arc
    
    **Z**: closepath
    
    define a path using the **d** attribute:
    
    ```html
    <svg width="500" height="500">
    <path d="M 0 0 L200 200 L200 0 Z" style="stroke:#000;
    	fill:none;" />
    </svg>
    ```
    
    M places our "virtual pen" down at the position 0, 0. It then moves 200px down and to the right, then moves up to the position 200, 0. The Z command closes the shape, which results in a hypotenuse:
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a6c7440e-2f94-40f6-9062-a257e8616845/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221133Z&X-Amz-Expires=86400&X-Amz-Signature=0e5d93070ea24f45a218e17ef9d2cad6833a06953ec6eda533582f9d7e4a3414&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    -   All of the above commands can also be expressed with lower case letters. When capital letters are used, it indicates absolute position; lower case indicates relative position.
-   Canvas element
    
    The HTML canvas is used to draw graphics that include everything from simple lines to complex graphic objects.
    
    canvas defined by:
    
    ```html
    <canvas id="canvas1" width="200" height="100">
    </canvas>
    ```
    
    -   note: The canvas element is only a container for graphics. You must use a script to actually draw the graphics (usually JavaScript).
    
    The canvas element must have an **id** attribute so it can be referred to by JavaScript:
    
    ```html
    <html>
       <head></head>
       <body>
         <canvas id="canvas1" 
       width="400" height="300"></canvas> 
    
       <script>
          var can = document.getElementById("canvas1"); 
          var ctx = can.getContext("2d");
       </script>
    
       </body>
    </html>
    ```
    
    getContext() returns a drawing context on the canvas.
    
    -   note: Basic knowledge of JavaScript is required to understand and use the Canvas.
        
    -   canvas coords
        
        The HTML canvas is a two-dimensional grid.
        
        The upper-left corner of the canvas has the coordinates (0,0).
        
        X coordinate increases to the right.
        
        Y coordinate increases toward the bottom of the canvas.
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e2c4087c-2788-400f-b686-039d3ab80adc/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221519Z&X-Amz-Expires=86400&X-Amz-Signature=6d50a931cac066297a3dbf1d0312823e8d5bf91acd9a92481642c86ce22d314c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        -   note: The canvas element is only a container for graphics.
    -   drawing shapes
        
        The **fillRect(x, y, w, h)** method draws a "filled" rectangle, in which w indicates width and h indicates height. The default fill color is black.
        
        A black 100\*100 pixel rectangle is drawn on the canvas at the position (20, 20):
        
        ```jsx
        var c=document.getElementById("canvas1");
        var ctx=c.getContext("2d");
        ctx.fillRect(20,20,100,100);
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d1704ec4-4758-4981-b445-9bcd4b965dfb/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221542Z&X-Amz-Expires=86400&X-Amz-Signature=f2c787d0a0112b30e31a2056d05fc21ea771474e7dcb144b31f8c257df6277f2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        The **fillStyle** property is used to set a color, gradient, or pattern to fill the drawing.
        
        Using this property allows you to draw a green-filled rectangle.
        
        ```jsx
        var canvas=document.getElementById("canvas1");
        var ctx=canvas.getContext("2d");
        ctx.fillStyle = "rgba(0, 200, 0, 1)";
        ctx.fillRect (36, 10, 22, 22);
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/24e647b2-ce5d-4129-b367-667b896aa058/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221554Z&X-Amz-Expires=86400&X-Amz-Signature=31236f22729882db4f6bb1479f4bc0dce4a2bbf070a389548e49497443624592&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        The canvas supports various other methods for drawing:
        
        **Draw a Line**
        
        moveTo(x,y): Defines the starting point of the line.
        
        lineTo(x,y): Defines the ending point of the line.
        
        **Draw a Circle**
        
        beginPath(): Starts the drawing.
        
        arc(x,y,r,start,stop): Sets the parameters of the circle.
        
        stroke(): Ends the drawing.
        
        **Gradients**
        
        createLinearGradient(x,y,x1,y1): Creates a linear gradient.
        
        createRadialGradient(x,y,r,x1,y1,r1): Creates a radial/circular gradient.
        
        **Drawing Text on the Canvas**
        
        Font: Defines the font properties for the text.
        
        fillText(text,x,y): Draws "filled" text on the canvas.
        
        strokeText(text,x,y): Draws text on the canvas (no fill).
        
        -   note: There are many other methods aimed at helping to draw shapes and images on the canvas.
-   svg vs. canvas
    
    **Canvas**
    
    -   Elements are drawn programmatically
    -   Drawing is done with pixels
    -   Animations are not built in
    -   High performance for pixels-based drawing operations
    -   Resolution dependent
    -   No support for event handlers
    -   You can save the resulting image as .png or .jpg
    -   Well suited for graphic-intensive games
    
    **SVG**
    
    -   Elements are part of the page's DOM (Document object model)
    -   Drawing is done with vectors
    -   Effects, such as animations are built in
    -   Based on standard XML syntax, which provides better accessibility
    -   Resolution independent
    -   Support for event handlers
    -   Not suited for game applications
    -   Best suited for applications with large rendering areas (for example, Google Maps)
    
    note: You can actually use both SVG and canvas on the same page, if needed. However, you cannot just draw SVG onto a canvas, or vice-versa.
    
-   canvas transformations
    
    -   translate
        
        The Canvas element can be transformed. As an example, a text is written on the canvas at the coordinates (10, 30).
        
        ```jsx
        ctx.font="bold 22px Tahoma";
        ctx.textAlign="start";
        ctx.fillText("start", 10, 30);
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e4d8a693-88aa-4059-92c2-b210d7b6b7d8/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221630Z&X-Amz-Expires=86400&X-Amz-Signature=a2d1258f9f0908ecd2dc503059490de2d2af5892f445ee30ca2571d1aa07d7c8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        The **translate(x,y)** method is used to move the Canvas.
        
        x indicates how far to move the grid horizontally, and y indicates how far to move the grid vertically.
        
        ```jsx
        ctx.translate(100, 150);
        ctx.fillText("after translate", 10, 30);
        ```
        
        In this example, the canvas is moved 100px to the right, and 150px down.
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3e4b26e3-d718-476d-8d06-bbe5b34ee4e1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221646Z&X-Amz-Expires=86400&X-Amz-Signature=c0932cecb8fc4567e3eae37bf93479520042e1fd020558f9340c6779f9e7a0f6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        -   note: Canvas has several methods for drawing paths, boxes, circles, text, and adding images.
    -   rotate
        
        The **rotate()** method is used to rotate the HTML5 Canvas. The value must be in _radians_, not degrees.
        
        Here is an example that draws the same rectangle before and after rotation is set:
        
        ```jsx
        ctx.fillStyle="#FF0000";
        ctx.fillRect(10, 10, 100, 100);
        
        ctx.rotate( (Math.PI / 180) * 25); //rotate 25 deg
        
        ctx.fillStyle="#0000FF";
        ctx.fillRect(10, 10, 100, 100);
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4dd35778-be81-47e7-956c-efbc8e620f69/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221704Z&X-Amz-Expires=86400&X-Amz-Signature=b295d7d7513a16f73c19425fee40e59f1b525d4cccaeeafd6cd9e8c773875723&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        -   note: The rotation will only affect drawings made after the rotation is done.
    -   scale
        
        The **scale()** method scales the current drawing. It takes two parameters:
        
        -   The number of times by which the image should be scaled in the X-direction.
        -   The number of times by which the image should be scaled in the Y-direction.
        
        ```jsx
        var canvas = document.getElementById('canvas1');
        ctx = canvas.getContext('2d');
        ctx.font="bold 22px Tahoma";
        ctx.textAlign="start";
        ctx.fillText("start", 10, 30);
        ctx.translate(100, 150);
        ctx.fillText("after translate", 0, 0);
        ctx.rotate(1);
        ctx.fillText("after rotate", 0, 0);
        ctx.scale(1.5, 4);
        ctx.fillText("after scale", 0, 20);
        ```
        
        This will scale the canvas 1.5 times in the X-direction, and 4 times in Y-direction:
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/97bf1729-bc5c-4b8c-b326-528d87e2f68d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T221722Z&X-Amz-Expires=86400&X-Amz-Signature=b6dde03658f973f3e72ef51d5147e627248564e3fb9de63e2cbaedaf56056af9&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        -   note: if you scale a drawing, all future drawings will also be scaled

```html
<!--Plus Sign!-->
<svg width="100" height="100">
	<line x1="50" y1="0" x2="50" y2="100"
	style="stroke:black;" />
	<line x1="0" y1="50" x2="100" y2="50"
	style="stroke:black;" />
</svg>
```