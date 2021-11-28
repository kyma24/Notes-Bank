-   changing attributes
    
    once elements have to work with have been selected, can change their attributes.
    
    As seen in the previous lessons, can change the text content of an element using the **innerHTML** property.
    
    Similarly, can change the attributes of elements.
    
    i.e. can change the src attribute of an image:
    
    ```html
    <img id="myimg" src="orange.png" alt="" />
    <script>
    	var el = document.getElementById("myimg");
    	el.src = "apple.png";
    </script>
    ```
    
    can use this to change the picture when something is changed, like when scrolled.
    
    can also change the href attribute of link:
    
    ```html
    <a href="<http://www.example.com>">Some Link</a>
    <script>
    	var el = document.getElementsByTagName("a");
    	el[0].href = "<http://www.sololearn.com>";
    </script>
    ```
    
    practically all attributes of an element can be changed using JS.
    
    ```jsx
    /* i.e. select all images of page and change their src attribute */
    
    var arr = document.getElementsByTagName("img");
    
    for(var x=0; x<arr.length; x++) {
    	arr[x].src = "demo.jpg";
    }
    ```