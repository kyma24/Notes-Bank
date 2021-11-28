-   the document Object
    
    there's a predefined **document** object in JS, which can be used to access all elements on the DOM.
    
    In other words, the **document** object is the owner(or **root**) of all objects in the webpage.
    
    So, if want to access objects in an HTML page, always start with accessing the document object.
    
    ```jsx
    document.body.innerHTML = "Some text";
    ```
    
    as **body** is an element of the DOM, we can access it using the **document** object and change the content of the **innerHTML** property.
    
    the **innerHTML** property can be used on almost all HTML elements to change its content.