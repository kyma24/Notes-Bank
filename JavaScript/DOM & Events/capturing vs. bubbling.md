-   capturing vs. bubbling
    
    the **addEventListener**() method allows to specify the propagation type with the "**useCapture**" parameter.
    
    ```jsx
    addEventListener(event, function, useCapture)
    ```
    
    the default value is **false**, which means the bubbling propagation is used; when the value is set to **true**, the event uses the capturing propagation
    
    ```jsx
    //capturing propagation
    elem1.addEventListener("click", myFunction, true);
    
    //bubbling propagation
    elem2.addEventListener("click", myFunction, false);
    ```
    
    this is particularly useful when have the same event handled for multiple elements in the DOM hierarchy.