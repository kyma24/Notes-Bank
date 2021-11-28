-   working with DOM
    
    each element in the DOM has a set of properties and methods that provide information abt their relationships in the DOM:
    
    element.**childNodes** returns an array of an element's child nodes.
    
    element.**firstChild** returns the first child node of an element.
    
    element.**lastChild** returns the last child node of an element.
    
    element.**hasChildNodes** returns true if an element has any child nodes, otherwise false.
    
    element.**nextSibling** returns the next node at the same tree level
    
    element.**previousSibling** returns the previous node at the same tree level.
    
    element.**parentNode** returns the parent node of an element.
    
    Can i.e. select all child nodes of an element and change their content:
    
    ```html
    <html>
    	<body>
    		<div id = "demo">
    			<p>some text</p>
    			<p>some other text</p>
    		</div>
    
    		<script>
    			var a = document.getElementById("demo");
    			var arr - a.childNodes;
    			for(var x = 0; x < arr.length; x++) {
    				arr[x].innerHTML = "new text";
    			}
    		</script>
    	</body>
    </html>
    ```