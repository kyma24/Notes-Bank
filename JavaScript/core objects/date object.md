-   setInterval()
    
    this method calls a function or evaluates an expression at specified intervals(in milsecs)
    
    it will continue calling the function until **clearInterval()** is called or the window is closed(like break)
    
    ```jsx
    //i.e.
    function myAlert() {
    	alert("Hi");
    }
    setInterval(myAlert, 3000);
    ```
    
    this will call the myAlert function every 3 seconds(1000 ms = 1 sec).
    
    write the name of the function without parentheses when passing it into the setInterval method.
    
-   Date
    
    the Date object enables the user to work with dates.
    
    a date consists of a year, a month, a day, and hour, a minute, a second, and milliseconds.
    
    using new Date(), create a new date object with the current date and time.
    
    ```jsx
    var d = new Date();
    //d stores the current date and time
    ```
    
    the other ways to initialize dates allow for the creation of new date objects from the **specified date and time**
    
    ```jsx
    new Date(milliseconds)
    new Date(dateString)
    new Date(year, month, day, hours, minutes, seconds, milliseconds)
    ```
    
    note that JS dates are calculated in milliseconds from 01 January 1970 00:00:00 Universal Time(UTC). One day contains 86,400,000 milliseconds.
    
    ```jsx
    //i.e.
    
    //Fri Jan 02 1970 00:00:00
    var d1 = new Date(86400000);
    
    //Fri Jan 02 2015 10:42:00
    var d2 = new Date("January 2, 2015, 10:42:00");
    
    //Sat Jun 11 1988 11:42:00
    var d3 = new Date(88,5,11,11,42,0,0);
    ```
    
    JS counts months from 0 to 11, like array indexes. January is 0, and December is 11.
    
    Date objects are static, rather than dynamic. The computer time is ticking, but date objects don't change, once created.
    
-   date methods
    
    when a Date object is created, a number of **methods** make it possible to perform operations on it.
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/854cd20b-9d42-4569-be44-b07541fb4cf6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T135815Z&X-Amz-Expires=86400&X-Amz-Signature=e354cf87818679bdef535257262c4b3706c430dec8c321f6c14b203fc2f62da9&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    ```jsx
    //i.e.
    var d = new Date();
    var hours = d.getHours();
    //hours is equal to the current hour
    ```
    
    create a program that prints the current time to the browser once every second.
    
    ```jsx
    function printTime() {
    	var d = new Date();
    	var hours = d.getHours();
    	var mins = d.getMinutes();
    	var secs = d.getSeconds();
    	document.body.innerHTML =
    hours+":"+mins+":"+secs;
    }
    setInterval(printTime, 1000);
    ```
    
    function **printTime()** was declared, which gets current time from the date object, and prints it to the screen.
    
    then called the function once every second, using the **setInterval** method.
    
    the **innerHTML** property sets or returns the HTML content of an element.
    
    in this case, the HTML content of the document's body is being changed. This overwrites the content every second, instead of printing it repeatedly to the screen.