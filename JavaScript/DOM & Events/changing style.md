-   changing style
    
    the style of HTML elements can also be changed using JS.
    
    All style attributes can be accessed using the style object of the element.
    
    ```html
    <div id="demo" style="width:200px">some text</div>
    <script>
    	var x = document.getElementById("demo");
    	x.style.color = "6600FF";
    	x.style.width = "100px";
    </script>
    ```
    
    code above changes the text color and width of the div element.
    
    all CSS properties can be set and modified using JS. Just remember that can't use dashes in property names. should be replaced with **camelCase** versions, where the compound words begin with a capital letter.
    
    i.e. the background-color property should be referred to as backgroundColor.
    
    ```jsx
    //i.e. to change the background color of all span elemnets of the page
    
    var s = document.getElementsByTagName("span");
    
    for(var x=0; x<s.length; x++) {
    	s[x].style.backgroundColor = "#33EA73";
    }
    ```