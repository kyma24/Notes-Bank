-   replacing elements
    
    to replace an HTML element, the element.replaceChild(newNode, oldNode) method is used.
    
    ```html
    <!-- i.e. -->
    <div id="demo">
    	<p id="p1">This is a paragraph.</p>
    	<p id="p2">This is another paragraph</p>
    </div>
    
    <script>
    	var p = document.createElement("p");
    	var node = document.createTextNode("This is new");
    	p.appendChild(node);
    
    	var parent = document.getElementsById("demo");
    	var child = document.getElementById("demo");
    	parent.replaceChild(p, child);
    </script>
    ```
    
    this code creates a new paragraph element that replaces the existing p1 paragraph.