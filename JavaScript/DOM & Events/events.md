-   events
    
    can write JS code that executes when an **event** occurs, such as when a user clicks on an HTML element, moves the mouse, or submits a form.
    
    When an event occurs on a target element, a **handler** function is executed(event handler). Common HTML events include:
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/023399c4-61dd-40e1-8583-a34c7df35860/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T140423Z&X-Amz-Expires=86400&X-Amz-Signature=7bff408b037b9a54e6446eec98da00ccabe804645d1331388621cac7ffc755ea&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    corresponding events can be added to HTML elements as attributes.
    
    i.e. \<p onclick="someFunc()">some text\</p>
    
    the **onload** and **onunload** events are triggered when the user enters or leaves the page. These can be useful when performing actions after the page is loaded.
    
    ```jsx
    <body onload="doSomething()">
    ```
    
    similarly, the **window.onload** event can be used to run code after the whole page is loaded.
    
    ```jsx
    window.onload = function() {
    	//some code
    }
    ```
    
    the **onchange** event is mostly used on textboxes. The event handler gets called when the text inside the textbox changes and focus is lost from the element.
    
    ```jsx
    <input type="text" id="name" onchange="change()">
    <script>
    	function change() {
    		var x = document.getElementById("name");
    		x.value = x.value.toUpperCase();
    	}
    </script>
    ```
    
    events are an essential part of dynamic web pages.