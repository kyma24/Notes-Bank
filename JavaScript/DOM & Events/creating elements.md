-   creating elements
    
    use the following methods to create new nodes.
    
    -   element.**cloneNode**() clones an element and returns the resulting node
    -   document.**createElement**(element) creates a new element node.
    -   document.**createTextNode**(text) creates a new text node.
    
    ```jsx
    //i.e.
    var node = document.createTextNode("Some new text");
    ```
    
    this will create a new text node, but won't appear on the document till append it to an existing element w/ one of the following methods:
    
    -   element.**appendChild(newNode)** adds a new child node to an element as the last child node
    -   element.**insertBefore(node1, node2)** inserts node 1 as a child before node 2.
    
    ```html
    <div id = "demo">some content</div>
    
    <script>
    	//creating a new paragraph
    	var p = document.createElement("p");
    	var node = document.createTextNode("Some new text");
    	
    	//adding the text to the paragraph
    	p.appendChild(node);
    
    	var div = document.getElementBy Id("demo");
    
    	//adding the paragraph to the div
    	div.appendChild(p);
    </script>
    ```
    
    this creates a new paragraph and adds it to the existing div element on the page.
    
    ```jsx
    //i.e. add a new <li> element to the unordered list w/ id="list"
    
    var el = document.createElement("li");
    
    var txt = document.createTextNode("B");
    el.appendChild(txt)
    
    var ul = document.getElementById("list");
    ul.appendChild(el);
    ```