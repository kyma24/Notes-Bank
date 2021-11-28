-   removing elements
    
    to remove an HTML element, must select the parent of the element and use the **removeChild**(node) method.
    
    ```html
    <div id = "demo">
    	<p id="p1">This is a paragraph.</p>
    	<p id="p2">This is another paragraph.</p>
    </div>
    
    <script>
    	var parent = document.getElementById("demo");
    	var child = document.getElementById("p1");
    	parent.removeChild(child);
    </script>
    ```
    
    this removes te paragraph w/ id = "p1" from the page.
    
    An alternative way of achieving the same result would be the use of the **parentNode** property to get the parent of the element want to remove:
    
    ```jsx
    var child = document.getElementById("p1");
    child.parentNode.removeChild(child);
    ```
    
    ```jsx
    //i.e. remove the node element from the page(par is node's parent)
    
    var par = document.getElementById("par");
    var node = document.getElementById("node");
    par.removeChild(node);
    ```