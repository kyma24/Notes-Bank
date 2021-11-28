-   handling events
    
    display an alert popup when the user clicks a specified button:
    
    ```html
    <button onclick="show()">Click Me</button>
    <script>
    	function show() {
    		alert("Hi there");
    	}
    </script>
    ```
    
    event handlers ca be assigned to elements.
    
    ```jsx
    var x = document.getElementById("demo");
    x.onclick = function() {
    	document.body.innerHTML = Date();
    }
    ```
    
    can also attach events to almost all HTML elements