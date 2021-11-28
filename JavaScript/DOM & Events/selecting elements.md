-   selecting elements
    
    all HTML elements are **objects**. And it is known that every object has **properties** and **methods**.
    
    The **document** object has methods that allows user to select the desired HTML element.
    
    These three methods are the most commonly used for selecting HTML elements:
    
    ```jsx
    //finds element by id
    document.getElementById(id)
    
    //finds elements by class name
    document.getElementByClassName(name)
    
    //finds elements by tag name
    document.getElementsByTagName(name)
    ```
    
    ```jsx
    //i.e. getElementById method is used to select the element with id="demo" and change its content:
    var elem = document.getElementById("demo");
    elem.innerHTML = "Hello World!";
    ```
    
    the **getElementsByClassName**() method returns a collection of all elements in the document with the specified class name.
    
    For example, if HTML page contained three elements with class="demo", the following code would return all those elements as an array:
    
    ```jsx
    var arr = document.getElementsByClassName("demo");
    //accessing the second element
    arr[1].innerHTML = "Hi";
    ```
    
    similarly, the **getElementsByTagName** method returns all of the elements of the specified tag name as an array.
    
    the following example gets all paragraph elements of the page and changes their content:
    
    ```jsx
    <p>hi</p>
    <p>hello</p>
    <p>hi</p>
    <script>
    var arr = document.getElementsByTagName("p");
    for (var x = 0; x < arr.length; x++) {
    	arr[x].innerHTML = "Hi there";
    }
    </script>
    ```
    
    the script will result in the following HTML:
    
    ```html
    <p>Hi there</p>
    <p>Hi there</p>
    <p>Hi there</p>
    ```