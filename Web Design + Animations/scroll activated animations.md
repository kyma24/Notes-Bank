-   scroll-activated animations
    -   basic idea
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b9c4f0e2-a2fe-464e-aa68-f42931a12376/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T153829Z&X-Amz-Expires=86400&X-Amz-Signature=59c93e31c0b225a75c99b2cc1cf62f61de256f849f4a4cf282760315f2f3e333&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        as you are scrolling, the subset of visible HTML elements will change
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1fa28232-1751-4e34-a463-71a80f012023/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T153850Z&X-Amz-Expires=86400&X-Amz-Signature=56a1f45f3914a3d56ae8dd4f0f0056ab681816fc035a8f6aabcd66375845c7b8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        depending on what kind of effect for this project, figuring out which elements are visible is important. There are 2 very closely related approaches you can take for this.
        
        One approach involves simply checking whether any part of an element is visible:
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/27ee62ad-20d6-4d50-beed-b10e03d002c3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T153902Z&X-Amz-Expires=86400&X-Amz-Signature=c546f93ba611f7679037c20b1ec2e1e6010409630924c59c2fdb367f73163223&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        The other approach involves checking whether an element is fully visible:
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4c75f76c-a5e8-4eed-80fc-33de19db27ff/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T153914Z&X-Amz-Expires=86400&X-Amz-Signature=d945881ab596cb5dee4e8e892072984279c5e07d3ab96afbcc8e2aa8498d8818&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
    -   modding the elements(example + explanation)
        
        now that the elements you want to affect are determined, we are going to do something about these elements.
        
        The generic solution revolves around setting a class value on those now-visible elements. Doing this serves only one purpose: to activate any CSS style rules that now get applied bc this class value got added to these elements. ← basic concept behind styling elements using JS.
        
        starting w/ list elements:
        
        ```html
        <ol id="myList">
          <li>One</li>
          <li>Two</li>
          <li>Three</li>
          <li>Four</li>
          <li>Five</li>
          <li>Six</li>
          <li>Seven</li>
          <li>Eight</li>
          <li>Nine</li>
          <li>Ten</li>
        </ol>
        ```
        
        these list elements will be styled by following style rules:
        
        ```css
        #myList li {
        	padding-left: 7px;
        	margin-bottom: 15px;
        	transition: all .2s ease-in-out;
        	transform: translate3d(0px, 30px, 0);
        	opacity: 0;
        }
        #myList li.active {
        	transform: translate3d(0px, 0, 0);
        	opacity: 1;
        }
        ```
        
        in the list items' current state, only the #myList li style rule is going to be applied on them. As you scroll some of these list items into view, we want these now-visible items to be styled a bit differently to set them apart from the non-visible list items. The way we do that is by giving these visible items a class value of **active**.
        
        ```html
        <ol id="myList">
        	<li class="active">One</li>
        	<li class="active">Two</li>
        	<li>Three</li>
        	<li>Four</li>
        	<li>Five</li>
        	<li>Six</li>
        	<li>Seven</li>
        	<li>Eight</li>
        	<li>Nine</li>
        	<li>Ten</li>
        </ol>
        ```
        
        the reason we do this isn't to have our elements look different in the HTML(it isn't our end goal). The end goal is to have them be styled differently, however. The moment our visible list elements get a class value of **active** set, the #myList li.active style rule becomes active on them. This is the crucial difference that separates our visible elements from our non-visible elements that don't have the active class set on them.
        
        The rest is extra. Specifically, what we see depends entirely on what the various applied CSS rules specify, whether you have any transitions applied, and whether any properties your transitions are listening for get modified. For the example, when the #myList li.active style rule gets applied to the visible list items, those items will smoothly fade-in and slide up. Why? bc of the **transition, transform, & opacity** properties in the classes.
        
        To visualize:
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7a77c172-2736-4e5e-a7ae-41968fc37e27/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T153950Z&X-Amz-Expires=86400&X-Amz-Signature=13dd62ccd3c5b994eaccacc33ec687d7c966f9e75feee11ef333f8172dc234c1&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        Note: what happens is directly related to what CSS properties are specified in the style rules. Fiddling w/ class values on visible elements is simply a signal. How your CSS reacts to that signal is entirely up to you, and you can very easily do many crazier things than just the simple slide and fade-in. Creating these scroll activated animations is just one part of the many possibilities.
        
    -   building it all out(implementing JS)
        
        -   listening to the scroll event
            
            first piece of JavaScript we will look at revolves around detecting when you are scrolling. Whenever you scroll your page using the scrollbar/fingers on a mobile device, you browser fires the **scroll** event. The most straightforward way to listen/deal w/ this event is by doing the following:
            
            ```jsx
            window.addEventListener("scroll", dealWithScrolling, false);
            
            function dealWithScrolling(e) {
            	//do stuff
            }
            ```
            
            each time you scroll your browser window, the dealWithScrolling event handler will get called.
            
            However, there is one big problem with this approach. This event is very chatty. It gets called at a very high frequency, so you want to avoid manipulating the DOM or doing something very computationally intensive by reacting to the scroll event each time it gets called. While we can't slow down how quickly our browser fires the scroll event, we can control the frequency with which we can react to it. You can use setTimeOut or setInterval to insert an artificial delay, but an even better solution is to peg our reactions to the frame rate. That can be done by relying on requestAnimationFrame.
            
            ```jsx
            var isScrolling = false;
            
            window.addEventListener("scroll", throttleScroll, false);
            
            function throttleScroll(e) {
            	if(isScrolling == false) {
            		window.requestAnimationFrame(function() {
            			dealWithScrolling(e);
            			isScrolling = false;
            		});
            	}
            	isScrolling = true;
            }
            
            function dealWithScrolling(e) {
            	//do stuff
            }
            ```
            
            the end result of code running is identical to the direct approach earlier. As content gets scrolled, the dealWithScrolling event handler will get called. The difference is that your event handler won't get called faster than the frame rate as determined by the requestAnimationFrame method. This means that your event handler code will get called around 60 times a second - which is a good upper bound for the sorts of DOM-related things that will happen anyway.
            
        -   detecting when elements are visible
            
            the only other snippets of code that are needed are for figuring out when elements are visible as you are scrolling around. To do this, there are 2 built-in helpers that we will rely on. The first one is getBoundingClientRect. This method returns the bounding box for whatever element we are interested in, and it provides position values for top, left, bottom, & right relative to the browser window's top left corner in addition to the width & height properties. The 2nd helper is the window.innerHeight and window.innerWidth properties that return our browser height & width respectively.
            
            ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/62417b6e-98e8-4566-b652-981f74abb126/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T155630Z&X-Amz-Expires=86400&X-Amz-Signature=fe3a5e07b447aa91f2ed09d7f9e7b862e3c295b9e222817f10006a12c8abe990&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
            
            -   detecting whether an element is partially visible
                
                to detect whether any part of an element we are interested in is visible, you have the isPartiallyVisible function.
                
                ```jsx
                function isPartiallyVisible(el) {
                	var elementBoundary = el.getBoundingClientRect();
                	
                	var top = elementBoundary.top;
                	var bottom = elementBoundary.bottom;
                	var height = elementBoundary.height;
                	
                	return ((top + height >= 0) && (height + window.innerHeight >= bottom));
                }
                ```
                
                to use the function pass in an element as an argument. If the element is partially visible, the function will return a true. Otherwise, the function will return a false.
                
            -   detecting whether an element is fully visible
                
                to detect whether an element is fully visible, we have the isFullyVisible function:
                
                ```jsx
                function isFullyVisible(el) {
                	var elementBoundary = el.getBoundingClientRect();
                	
                	var top = elementBoundary.top;
                	var bottom = elementBoundary.bottom;
                
                	return ((top >= 0) && (bottom <= window.innerHeight));
                }
                ```
                
                the function works very similar to the isPartiallyVisible function. If the element we are checking is fully visible, the function will return true. Otherwise, it will return false.
                
    -   full code example(concepts so far)
        
        ```jsx
        <!DOCTYPE html>
        <html>
         
        <head>
          <meta name="viewport" content="width=device-width, initial-scale=1.0" />
          <title>Change Color on Scroll</title>
         
          <style>
            body {
              background-color: #FDE74C;
              transition: all 1s ease-in;
              padding: 50px;
              color: #111;
              font-family: sans-serif;
              line-height: 32px;
              font-size: 18px;
            }
         
            h1 {
              font-family: sans-serif;
            }
         
            .colorOne {
              background-color: #9BC53D;
              color: #000;
            }
         
            .colorTwo {
              background-color: #FFF;
              color: #000;
            }
         
            #mainContent {
              width: 420px;
              margin: 0 auto;
            }
         
            #mainContent p {
              padding: 20px;
            }
         
            #mainContent #firstBox {
              font-weight: bold;
              transform: translate3d(-30px, 0, 0);
              transition: all .5s ease-out;
              opacity: 0;
            }
         
            #mainContent #firstBox.active {
              background-color: #333;
              color: #FFF;
              transform: translate3d(0, 0, 0);
              opacity: 1;
            }
         
            #mainContent #secondBox {
              transition: all .2s ease-in-out;
              transform: translate3d(0, 30px, 0);
              opacity: 0;
            }
         
            #mainContent #secondBox.active {
              background-color: #1581AF;
              color: #FFF;
              transform: translate3d(0, 0, 0);
              opacity: 1;
            }
         
            #mainContent ol li {
              padding-left: 7px;
              margin-bottom: 15px;
              transition: all .2s ease-in-out;
              transform: translate3d(20px, 0, 0);
              opacity: 0;
            }
         
            #mainContent ol li.active {
              transform: translate3d(0px, 0, 0);
              opacity: 1;
            }
          </style>
        </head>
         
        <body>
          <div id="mainContent">
            <h1>Scroll Down</h1>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur quis massa a arcu efficitur suscipit vehicula et risus.</p>
            <ol id="myList">
              <li>Nam sagittis est non enim ultrices elementum. </li>
              <li>Sed id ligula sed mi tempor ornare.</li>
              <li>Aenean feugiat risus eget sagittis volutpat. Proin quis orci a metus lacinia auctor eget id nisi.</li>
              <li>Donec pulvinar nunc feugiat semper consequat.</li>
              <li>Etiam cursus justo eget libero gravida, nec faucibus mauris posuere.</li>
              <li>In nec sem id libero egestas cursus vel a urna.</li>
              <li>Fusce pulvinar arcu eu lobortis egestas. Maecenas eleifend felis ut urna consectetur, et pellentesque mi molestie.</li>
              <li>Aliquam ut felis venenatis, dapibus ante non, gravida nulla.</li>
              <li>Donec consectetur quam in urna commodo, sed aliquet metus vehicula.</li>
              <li>Mauris eget est sit amet felis eleifend sagittis non id nulla.</li>
            </ol>
            <p id="firstBox">Phasellus tortor nisl, dapibus at posuere sed, tempor in massa. Pellentesque eu sodales orci, finibus congue libero. Mauris molestie bibendum posuere.</p>
            <p>Nunc blandit varius sapien quis ultrices. Vestibulum et consequat augue. Pellentesque et maximus nisl, sit amet dictum ante.</p>
            <p id="secondBox">Nullam magna augue, consequat eu augue ut, volutpat fringilla est. Ut commodo ac magna vulputate dictum.</p>
          </div>
         
          <script>
            var isScrolling = false;
         
            window.addEventListener("scroll", throttleScroll, false);
         
            function throttleScroll(e) {
              if (isScrolling == false) {
                window.requestAnimationFrame(function() {
                  scrolling(e);
                  isScrolling = false;
                });
              }
              isScrolling = true;
            }
         
            document.addEventListener("DOMContentLoaded", scrolling, false);
         
            var listItems = document.querySelectorAll("#mainContent ol li");
            var firstBox = document.querySelector("#firstBox");
            var secondBox = document.querySelector("#secondBox");
         
            function scrolling(e) {
         
              if (isPartiallyVisible(firstBox)) {
                firstBox.classList.add("active");
         
                document.body.classList.add("colorOne");
                document.body.classList.remove("colorTwo");
              } else {
                document.body.classList.remove("colorOne");
                document.body.classList.remove("colorTwo");
              }
         
              if (isFullyVisible(secondBox)) {
                secondBox.classList.add("active");
         
                document.body.classList.add("colorTwo");
                document.body.classList.remove("colorOne");
              }
         
              for (var i = 0; i < listItems.length; i++) {
                var listItem = listItems[i];
         
                if (isPartiallyVisible(listItem)) {
                  listItem.classList.add("active");
                } else {
                  listItem.classList.remove("active");
                }
              }
            }
         
            function isPartiallyVisible(el) {
              var elementBoundary = el.getBoundingClientRect();
         
              var top = elementBoundary.top;
              var bottom = elementBoundary.bottom;
              var height = elementBoundary.height;
         
              return ((top + height >= 0) && (height + window.innerHeight >= bottom));
            }
         
            function isFullyVisible(el) {
              var elementBoundary = el.getBoundingClientRect();
         
              var top = elementBoundary.top;
              var bottom = elementBoundary.bottom;
         
              return ((top >= 0) && (bottom <= window.innerHeight));
            }
          </script>
        </body>
         
        </html>
        ```
        
    -   performance considerations
        
        having your content animate in and out while scrolling is only good if it doesn't negatively affect performance. If you run a performance profile on the example in a browser's performance tools, you'll see the frame rate stays pretty consistently around 60fps, which is good.
        
        But that doesn't mean that the code is perfect. There are some possible optimizations that wasn't done at the risk of overoptimizing something whose performance is already good. i.e. calling getBoundingClientRect is both slow and causes repaints. Checking window.innerHeight triggers a repaint as well. There are somewhat tricky solutions out there to work around these issues, but at the risk of not unnecessarily optimizing what is already 60fps, the code leaves these 2 problematic things as-is.
        
        Lastly, listening to the scroll event(& most touch events) has its own set of issues. Most browsers optimize page scrolling heavily, but listening for a scroll or touch-related event ends up negating these optimizations. The reason has to do w/ event handlers. We can ignore a page scroll by listening to a mouse scroll or touch event and calling preventDefault. This means if there are any event handlers associated with the mouse scroll/touch, the browser has to wait to fully execute any JavaScript associated with that event handler. This is despite most event handlers of this sort never actually cancel the scrolling. This verification can and often does drag down performance.
        
        A partial work around is to not listen to the mouse scroll event and instead use requestAnimationFrame and constantly poll the position of all of our elements that we want scrolled into our out of view. While that seems to solve the browser scroll optimization problem, that didn't result in any meaningful performance gains. Worse, having getBoundingClientRect & window.innerheight getting called 60 times a second even if there is no scrolling/style-related changes turned out to create unnecessary work. Obviously, all of this doesn't help with touch events at all.
        
        These issues are also being resolved. Some under-development features are:
        
        i. Passive Event listeners
        
        This features an event handler to specify, among other things, whether it will cancel a scroll or not. This means your browser can safely optimize scroll performance even if you have event handlers. For extra bonus, you can combine passive event listeners w/ pointer events to ensure touch events behave even better.
        
        ii. IntersectionObserver
        
        A bulk of the code revolves around detecting whether an element is fully or partially visible as you scroll. This involves, like mentioned, expensive operations like getBoundingClientRect & window.innerHeight. The IntersectionObserver API solves this by bypassing these expensive operations. Instead, it provides specialized functionality for really efficiently detecting where an element is in relation to what you see on the screen.