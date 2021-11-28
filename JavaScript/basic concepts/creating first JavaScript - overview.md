```html
<!-- On the web, JavaScript code lives inside HTML document. -->
<script>
<!-- ... -->
</script>
```

note: can put **script** tag anywhere in HTML doc, usually on the bottom-ish

-   Hello World - document.write()
    
    ```jsx
    <script>
    	document.write("Hello World!");
    	//JS document.write() = Python print()
    	//can also use some HTML tags
    	document.write("<h1>Hello World!</h1>");
    </script>
    ```
    
    note: document.write() should only be used for testing. There are better output mechanisms in JS
    
-   Output to console - console.log()
    
    console is part of the web browser and allows you to log messages, run JavaScript code, & see errors & warnings.
    
    (written in language NODE.js)
    
    ```
    console.log("Hello from console!")
    ```
    
    note: developers mostly use the console to test JavaScript code.
    
-   comments(same as Java/CSS) - alert()
    
    ```jsx
    //This is a single line comment
    alert("This is an alert box!");
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e14173c5-2b4a-47df-852c-066fe9c3dc12/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T133148Z&X-Amz-Expires=86400&X-Amz-Signature=ff487aa96d133c5ed6d4ce9d15be32fc9220cdec52954e0e4f00b3f2b3e29c0c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    note: alert is used to create a message box