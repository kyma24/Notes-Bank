-   web storage API
    
    `HTML web storage allows website to download/store data on user's computer`
    
    `before, had to use (JavaScript) cookies to store data`
    
    **advantages**
    
    -   more secure
    -   faster
    -   can store more data
    -   stored data is not sent w/ every server request
    
    ❗ \*\*\*\*Local storage is per **domain**. All pages from **one domain** can _store and access the same data_
    
    2 types of web storage **objects** :
    
    -   sessionStorage(), and
    -   localStorage()
    
    local vs session\*\*:\*\*
    
    -   **session** storage stores data within the session and deletes it after the session ends(like RAM)
    -   **local** storage stores data for an (infinite) period of time
    
    ❗ basic JavaScript familiarity is necessary to understand/use **API**(application programming interface: defines interactions between multiple software intermediaries. It defines the kinds of calls or requests that can be made, how to make them, the data formats that should be used, the conventions to follow, etc.)
    
    local & session storage syntax is very similar(and simple): stored as key/value pairs
    
    ```jsx
    //**STORING A VALUE**
    localStorage.setItem("key1", "value1");
    ```
    
    ```jsx
    //**GETTING A VALUE**(printing it)
    ****alert(localStorage.getItem("key1"));
    ```
    
    ```jsx
    //**REMOVING A VALUE**
    localStorage.removeItem("key1");
    ```
    
    ```jsx
    //**REMOVING ALL VALUES**
    localStorage.clear();
    ```
    
    ❗ note: same syntax is used w/ session storage, except instead of "localStorage" it becomes "sessionStorage"
    
    don't need to know too much on this topic just yet; after doing CSS & JavaScript, this will be easier to understand
    
    i.e.
    
    ```jsx
    //clear all values stored in the localStorage, then store "a" using the key "b"
    localStorage.**clear**();
    
    localStorage.
    	setItem(**"b"**, **"a"**);
    ```
    
-   geolocation API
    
    basics:
    
    -   as stated in the title, the geolocation API is used to obtain the user's geographical location
    -   this could risk leaking private info, so this function is not useable until user agrees
    -   geolocation is a lot more accurate for devices/computers with GPS
    
    using HTML geolocation:
    
    -   Geolocation API main method is getCurrentPosition: retrieves current geographic location of user's device
    
    ```jsx
    navigator.geolocation.getCurrentPosition();
    ```
    
    parameters:
    
    -   **showLocation** - _mandatory_: defines callback method that retrieves location information.
    -   **errorHandler** - _optional_: defines callback method that is called(invoked) when an error occurs in processing the \[asynchronous\] call.
    -   **options** - _optional_: defines set of options for retrieving location info
    
    ❗ remember: it's fine if it isn't quite understandable yet; must have basic JavaScript knowledge to fully understand
    
    presenting the data:
    
    user location can be presented in 2 ways:
    
    -   **geodetic** way: describes position w/ latitude & longitude
    -   **civic** representation: presented in a format that is easier for us to read
    
    every parameter has both a geodetic & civic representation or counterpart:
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/41191f30-3176-4fba-b066-d923bc163f3e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T220938Z&X-Amz-Expires=86400&X-Amz-Signature=f1a5d3558fc242bcb975b42098ed93a22a671933a1e5fd6341d71b4ade663960&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    ❗ note: getCurrentPosition method returns an object if successful. always returns latitude/longitude and accuracy properties
    
-   drag & drop API
    
    this feature allows you to grab onto \[any\] HTML element and drag it around/drop it in a given area
    
    to make an item draggable, just assign boolean value of "true" to the "draggable" attribute
    
    ```html
    <img draggable="true" />
    ```
    
    the API for drag-and-drop is **event-based**.
    
    ```html
    <!DOCTYPE HTML>
    <html>
       <head>
       <script>
    function allowDrop(ev) {
        ev.preventDefault();
    }
    
    function drag(ev) {
        ev.dataTransfer.setData("text", ev.target.id);
    }
    
    function drop(ev) {
        ev.preventDefault();
        var data = ev.dataTransfer.getData("text");
        ev.target.appendChild(document.getElementById(data));
    }
       </script>
       </head>
    <body>
    
       <div id="box" **ondrop**="drop(event)"
       **ondragover**="allowDrop(event)"
       style="border:1px solid black; 
       width:200px; height:200px"></div>
    
       <img id="image" src="sample.jpg" **draggable**="true"
       **ondragstart**="drag(event)" width="150" height="50" alt="" />
    
    </body>
    </html>
    ```
    
    let's elaborate on the **bolded** terms in the code:
    
    **What to Drag**
    
    When the element is dragged, the **ondragstart** attribute calls a function, drag(event), which specifies what data is to be dragged. The **dataTransfer.setData()** method sets the data type and the value of the dragged data.
    
    ```jsx
    function drag(ev) {
        ev.dataTransfer.setData("text", ev.target.id);
    }
    ```
    
    in this example, the data type is "text" and the value is the ID of the draggable element ("image").
    
    **Where to Drop**
    
    The **ondragover** event specifies where the dragged data can be dropped. By default, data and elements cannot be dropped in other elements. To allow a drop, we must prevent the default handling of the element. This is done by calling the event. **preventDefault**() method for the **ondragover** event.
    
    **Do the Drop**
    
    When the dragged data is dropped, a drop event occurs. In the example above, the **ondrop** attribute calls a function, drop(event).
    
    ```jsx
    function drop(ev) {
        ev.preventDefault();
        var data = ev.dataTransfer.getData("text");
        ev.target.appendChild(document.getElementById(data));
    }
    ```
    
    The **preventDefault()** method prevents the browser's default handling of the data (default is open as link on drop). The dragged data can be accessed with the **dataTransfer.getData()** method. This method will return any data that was set to the same type in the setData() method. The dragged data is the ID of the dragged element ("image"). At the end, the dragged element is appended into the drop element, using the appendChild() function.