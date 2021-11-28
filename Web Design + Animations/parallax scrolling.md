-   parallax scrolling
    -   intro to the PARALLAX EFFECT
        
        -   need a way to independently move background elements & content when entire page is scrolled, by **layering**. We layer background elements directly behind content.
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d5d08568-3e5e-4619-8f3d-b5541c84efb4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T155750Z&X-Amz-Expires=86400&X-Amz-Signature=bdedca9992bf987eb14cfe6e4aff42d1009b29847079c776f841a74fc097db53&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        -   there are several reasons why we do this:
            
            a. first, content will not interfere in any way w/ what is happening "behind the scenes"
            
            b. second, you can squeeze a lot of performance by doing this.
            
            c. lastly, and very importantly, w/ this arrangement, when you scroll browser window, the content position & background elements' positions can be adjusted independently very easily.
            
            ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c3fb43a0-9eff-463b-b5dd-e2153a6b019e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T155807Z&X-Amz-Expires=86400&X-Amz-Signature=dee92a7fc42fc56b67d51d76930502178a1e570672c67cfd62069f083073bfa1&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
            
            next thing is scrolling itself.
            
            -   3 ways to scroll content in browser: by using scrollbars, mouse wheel, (for mobile devices) fingers, and up/down/PgUp/PgDn/etc. keys on keyboard.
            -   no matter how one scrolls, when it happens, everything on page moves up or down by default. amount they move may vary depending on whether you used the scrollbar, fingers, mouse wheel, or keyboard; rest assured that everything on you page **will** move.
                -   However, in this case, we don't want our background elements to automatically move when we scroll browser. We want to control how much background elements scroll & in which direction ourselves.
            
            simple solution: prevent background elements from scrolling w/ rest of page.
            
            ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/dede1147-bc0e-4c2d-8e74-ad67d8155b25/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T155823Z&X-Amz-Expires=86400&X-Amz-Signature=9c15ba1ecc80cd83010ecccc312b5815302085ada6de95d3836592864ef48efe&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
            
    -   code w/ explanations
        
        -   getting started(HTML)
            
            -   below code is pretty simple and understandable:
                
                \[metadata tag explanation\]([https://www.w3schools.com/tags/tag\_meta.asp#:~:text=The tag defines metadata about an HTML document.&text=Metadata is used by browsers,)%2C and other web services.)](https://www.w3schools.com/tags/tag_meta.asp#:~:text=The%20tag%20defines%20metadata%20about%20an%20HTML%20document.&text=Metadata%20is%20used%20by%20browsers,)%2C%20and%20other%20web%20services.))
                
            
            ```html
            <!DOCTYPE html>
            <html>
             
            <head>
            <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
            <title>Parallax Scrolling Example</title>
            <style>
                body {
                    background-color: #EEE;
                }
                #content {
                    padding: 50px;
                    margin: 40px;
                    background-color: rgba(255, 255, 255, .48);
                    text-align: center;
                }
                #content p {
                    font-family: Helvetica, sans-serif;
                    font-size: 28px;
                    line-height: 40px;
                    color: #111;
                }
                h1 {
                    text-transform: capitalize;
                    font-family: sans-serif;
                    font-size: 40px;
                    padding: 10px;
                    margin: 40px;
                    background-color: rgba(20, 20, 20, .8);
                    color: #FFF;
                }
            </style>
            </head>
             
            <body>
             
            <h1>Parallaxing!</h1>
            <div id="content">
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
                <p>All work and no play makes Jack a dull boy</p>
            </div>
             
            <script>
             
            </script>
            </body>
            </html>
            ```
            
            above code will be w/o the background elements & the parallax effect. These things will be explained.
            
        -   adding background elements(CSS)
            
            -   our background elements are nothing more than div elements that are absolutely positioned. In HTML **just above the opening** script **tag, add following lines:**
            
            ```html
            <div id="bigYellowCircle"></div>
            <div id="blueSquare"></div>
            <div id="greenPentagon"></div>
            ```
            
            What we are doing is adding 3 div elements each w/ id value of bigYellowCircle, blueSquare, and greenPentagon. There isn't much going on here yet, since we have yet to do the real work in CSS.
            
            Next, inside style region, add following style rules:
            
            ```html
            #bigYellowCircle {
                background-image: url("<https://www.kirupa.com/images/yellow_circle.svg>");
                background-repeat: no-repeat;
                background-position: center center;
                background-size: 90%;
                position: fixed;
                top: 0;
                width: 100vw;
                height: 100vw;
                z-index: -1;
                opacity: .75;
            }
            #blueSquare {
                background-image: url("<https://www.kirupa.com/images/blue_square.svg>");
                background-repeat: no-repeat;
                background-position: 97% bottom;
                background-size: 10%;
                position: fixed;
                top: 0;
                width: 100vw;
                height: 100vw;
                z-index: -2;
                opacity: .75;
            }
            #greenPentagon {
                background-image: url("<https://www.kirupa.com/images/green_pentagon.svg>");
                background-repeat: no-repeat;
                background-position: 5% top;
                background-size: 50%;
                position: fixed;
                top: 0;
                width: 100vw;
                height: 100vw;
                z-index: -3;
                opacity: .75;
            }
            ```
            
            These style rules affect 3 div elements we just added, & take a look @ the properties we are setting on them. The shapes that are seen are just background images. Each div element takes up full size of viewport, & we adjust position & size of each background image to give us full effect.
            
            If you run code right now, background images will scroll.
            
            Back to CSS.
            
            The way to ensure background elements stay fixed is using position CSS property w/ value of fixed(Learned in CSS).
            
            To ensure background elements appear behind content, we set the z-index property to a negative value for each of our div elements(also learned).
            
            All that remains is the JAVASCRIPT.
            
        -   the JavaScript(explanation of what we will do)
            
            inside script tags, we'll add code that will:
            
            a. listen for our current scroll position
            
            b. slid our background elements up/down using a **translate3d** transform w/ vertical values(learned) based on current scroll position
            
        -   referencing our background elements(JS)
            
            the first thing to do is reference background elements in code so that we can access them easily. Inside script tags, add following 3 lines:
            
            ```jsx
            var bigYellowCircle = document.querySelector("#bigYellowCircle");
            var blueSquare = document.querySelector("#blueSquare");
            var greenPentagon = document.querySelector("#greenPentagon");
            ```
            
            This should be pretty straightforward: we are storing our bigYellowCircle, blueSquare, & greenPentagon elements in variables of the same name using some help from the **querySelector** method.
            
        -   helper function for setting the position(JS)
            
            once again, we will be shifting our background elements using a translate3d transform(learned: if don't know how to set, reference CSS)
            
            What we need to do is create a JS version that allows us to do the same thing. To do that, below our existing code, add the following:
            
            ```jsx
            function setTranslate(xPos, yPos, el) {
            	el.style.transform = "translate3d(" + xPos + "," + yPos + "px, 0)";
            }
            ```
            
            We just added a function called setTranslate, and it takes 3 arguments. The horizontal position, vertical position, and element to set the transform on. There are a bunch of quotation marks and stuff to allow us to recreate the translate3d transform while allowing the numerical values to be specified by our arguments. It works!
            
            -   ES6 Template Literals alternative
                
                note: if you don't like having to compose strings using all of those quotation marks, you may like ES6 template literals a lot. The above setTranslate function using template literals will look like this:
                
                ```jsx
                function setTranslate(xPos, yPos, el) {
                	el.style.transform = `translate3d(${xPos}px, ${yPos}px, 0)`;
                }
                ```
                
                It looks much cleaner, but the browser support is limited to only the newest releases. May have to use prefixes, or have to wait to support older browsers as well.
                
        -   getting scroll position(JS)
            
            most complex part of code deals w/ getting scroll position and using that to update the position of our background elements. First thing we'll do is add the code for getting the scroll position.
            
            Go ahead and add the following:
            
            ```jsx
            window.addEventListener("DOMContentLoaded", scrollLoop, false);
             
            var xScrollPosition;
            var yScrollPosition;
             
            function scrollLoop() {
                xScrollPosition = window.scrollX;
                yScrollPosition = window.scrollY;
             
                requestAnimationFrame(scrollLoop);
            }
            ```
            
            There are a few things that happen w/ this code: first thing we do is call a function named scrollLoop when our page's DOM has been loaded:
            
            ```jsx
            window.addEventListener("DOMContentLoaded", scrollLoop, false);
            ```
            
            This is all done by relying on the DOMContentLoaded event. The scrollLoop function is where all the magic happens, so let's look at that one:
            
            ```jsx
            var xScrollPosition;
            var yScrollPosition;
            
            function scrollLoop() {
            	xScrollPosition = window.scrollX;
            	yScrollPosition = window.scrollY;
            
            	requestAnimationFrame(scrollLoop);
            }
            ```
            
            We store the current scroll position in our xScrollPosition & yScrollPosition variables by accessing the window.scrollX & the window.scrollY properties. Bc these properties will change as we scroll our page, we need a way to keep our xScrollPosition and yScrollPosition variables up-to-date. That is where the requestAnimationFrame call comes in. It ensures that we call our scrollLoop function every time our screen is ready to update - no slower, no faster.
            
            Only missing thing is the part where we use this data to adjust position of background elements. To take care of that, add following bolded lines:
            
            ```jsx
            function scrollLoop() {
            	xScrollPosition = window.scrollX;
            	yScrollPosition = window.scrollY;
            
            	setTranslate(0, yScrollPosition * -0.2, bigYellowCircle);
            	setTranslate(0, yScrollPosition * -1.5, blueSquare);
            	setTranslate(0, yScrollPosition * .5, greenPentagon);
            
            	requestAnimationFrame(scrollLoop);
            }
            ```
            
            In these lines, we are calling the setTranslate function & passing in the values for the horizontal & vertical positions and element to apply to our translate3d transform to. Bc we aren't shifting our background elements horizontally, the first argument is just 0. The second argument is where we pass our current vertical scroll position(aka yScrollPosition), and we multiply our position by a scale factor to adjust how fast, how slow, or in what direction our background elements will actually move. W/ these scale factors, you have a lot of room for experimentation. With that, the code should start working perfectly :D
            
    -   final code
        
        ```html
        <!DOCTYPE html>
        <html>
         
        <head>
        <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
        <title>Parallax Scrolling Example</title>
        <style>
            body {
                background-color: #EEE;
            }
            #content {
                padding: 50px;
                margin: 40px;
                background-color: rgba(255, 255, 255, .48);
                text-align: center;
            }
            #content p {
                font-family: Helvetica, sans-serif;
                font-size: 28px;
                line-height: 40px;
                color: #111;
            }
            h1 {
                text-transform: capitalize;
                font-family: sans-serif;
                font-size: 40px;
                padding: 10px;
                margin: 40px;
                background-color: rgba(20, 20, 20, .8);
                color: #FFF;
            }
            #bigYellowCircle {
                background-image: url("<https://www.kirupa.com/images/yellow_circle.svg>");
                background-repeat: no-repeat;
                background-position: center center;
                background-size: 90%;
                position: fixed;
                top: 0;
                width: 100vw;
                height: 100vw;
                z-index: -1;
                opacity: .75;
            }
            #blueSquare {
                background-image: url("<https://www.kirupa.com/images/blue_square.svg>");
                background-repeat: no-repeat;
                background-position: 97% bottom;
                background-size: 10%;
                position: fixed;
                top: 0;
                width: 100vw;
                height: 100vw;
                z-index: -2;
                opacity: .75;
            }
            #greenPentagon {
                background-image: url("<https://www.kirupa.com/images/green_pentagon.svg>");
                background-repeat: no-repeat;
                background-position: 5% top;
                background-size: 50%;
                position: fixed;
                top: 0;
                width: 100vw;
                height: 100vw;
                z-index: -3;
                opacity: .75;
            }
        </style>
        </head>
         
        <body>
         
        <h1>Parallaxing!</h1>
        <div id="content">
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
            <p>All work and no play makes Jack a dull boy</p>
        </div>
         
        <div id="bigYellowCircle"></div>
        <div id="blueSquare"></div>
        <div id="greenPentagon"></div>
         
        <script>
            var bigYellowCircle = document.querySelector("#bigYellowCircle");
            var blueSquare = document.querySelector("#blueSquare");
            var greenPentagon = document.querySelector("#greenPentagon");
         
            function setTranslate(xPos, yPos, el) {
                el.style.transform = "translate3d(" + xPos + ", " + yPos + "px, 0)";
            }
         
            window.addEventListener("DOMContentLoaded", scrollLoop, false);
         
            var xScrollPosition;
            var yScrollPosition;
         
            function scrollLoop() {
                xScrollPosition = window.scrollX;
                yScrollPosition = window.scrollY;
         
                setTranslate(0, yScrollPosition * -0.2, bigYellowCircle);
                setTranslate(0, yScrollPosition * -1.5, blueSquare);
                setTranslate(0, yScrollPosition * .5, greenPentagon);
         
                requestAnimationFrame(scrollLoop);
            }
         
        </script>
        </body>
        </html>
        ```