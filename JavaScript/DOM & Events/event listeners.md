-   event listeners
    
    the **addEventListener()** method attaches an event handler to an element without overwriting existing event handlers. Can add many event handlers to one element.
    
    Can also add many event handlers of the same type to one elemnet, i.e. two "click" events.
    
    ```jsx
    element.addEventListener(event, function, useCapture);
    ```
    
    the first parameter is the element's type(like "click" or "mousedown").
    
    The second parameter is the function we want to call when the event occurs
    
    the third parameter is a Boolean value specifying whether to use event **bubbling** or event **capturing**. This parameter is optional.
    
    Note that don't use the "**on**" prefix for this event; use "click" instead of "onclick"
    
    ```jsx
    //i.e.
    event.addEventListener("click", myFunction);
    element.addEventListener("mouseover", myFunction);
    
    function myFunction() {
    	alert("Hello World!");
    }
    ```
    
    this adds 2 event listeners to the element.
    
    Can remove one of the listeners.
    
    ```jsx
    element.removeEventListener("mouseover", myFunction);
    ```
    
    create an event handler that removes itself after being executed:
    
    ```jsx
    <button id="demo">Start</button>
    
    <script>
    	var btn = document.getElementById("demo");
    	btn.addEventListener("click", myFunction);
    	
    	function myFunction() {
    		alert(Math.random());
    		btn.removeEventListener("click", myFunction);
    	}
    </script>
    ```
    
    after clicking the button, an alert with a random number displays and the event listener is removed.
    
    note that Internet Explorer version 8 and lower don't support the **addEventListener**() and **removeEventListener**() methods. However, can use the document.**attachEvent**() method to attach event handlers in IE.