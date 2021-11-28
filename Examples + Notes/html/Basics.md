-   Basics: 12/22/2020 - basic formatting
    
    ```html
    <!DOCTYPE html>
    <html>
      <head>
      </head>
      <body>
        <p>This is a <br /> line break</p>
        <!-- ^^no need for ending for break -->
        <!-- break can also be <br> -->
        <!-- similarly, horizontal lines can either be <hr> or <hr />: means thematic break -->
    
        <!-- Text formatting: -->
        <p>This is regular text </p>
        <p><b>bold text </b></p>
        <p><big> big text </big></p>
        <p><i> italic text </i></p>
        <p><small> small text </small></p>
        <p><strong> strong text </strong></p>
        <p><sub> subscripted text </sub></p>
        <p><sup> superscripted text </sup></p>
        <p><ins> inserted text </ins></p>
        <p><del> deleted text </del></p>
        <!-- Browsers display <strong> as <b>, and <em> as <i>. However, the meanings of these tags differ: <b> and <i> define bold and italic text, respectively, while <strong> and <em> indicate that the text is "important". -->
    
        <!-- headings -->
        <h1>This is heading 1</h1>
        <h2>This is heading 2</h2>
        <h3>This is heading 3</h3>
        <h4>This is heading 4</h4>
        <h5>This is heading 5</h5>
        <h6>This is heading 6</h6>
        <!-- biggest to smallest: 1-6 -->
        <!-- Don't use headings to make things big/bold: structure will be formatted differently by search engine -->
      </body>
    </html>
    ```
    
-   Basics: 12/24/2020 - image & border
    
    ```html
     <!DOCTYPE html>
    <html>
      <head>
      </head>
      <body>
    
    		<hr width = "50 px" /> <!-- the last backslash is optional-->
    		<hr width = "50%" /> <!-- this statement has the same output as the one above-->
    		
    		<p align= "center">This is text<br />
    			<hr width= "10%" align = "right" /> This is also a text.
    		</p> <!-- The align attribute of <p> is not supported in HTML5.-->
    
    		<p align = "center">
    			This is text
    			<hr width="50%" aligh ="left" />
    		</p>
    		<!-- contradictory code: in the end, the contradictory statements run separately(outputs "This is text" in center, then a halved-line on the left side below that) -->
    
    		<img src="image.jpg" alt="" /> <!-- insert address(image location, whether local or online) inside quotation marks. no closing statement, only contains attributes; src attribute defines image URL -->
    		<!-- alt attribute specifies an alternate text for an image(describes image in words, in case image can't be displayed. is required.-->
    
    		<img src="tree.jpg" height= "50%" width = "50%" border"1px" alt= "" /> <!-- of course, can use pixels instead(150px)-->
    		<!-- border: by default, image has no border. border attribute specifies the width of border around image -->
    
     
    	</body>
    </html>
    ```
    
-   Basics: 12/25/2020 - links, tables, & element types
    
    -   links
        
        ```html
        <a href="" target= "_blank"></a>
        <!-- text that you want link to be embedded in: insert between the tag and the ending -->
        <!-- target attribute specifies where to open linked doc -->
        <!-- assigning "_blank" value to target attribute will open a new tab/window when click on link -->
        
        <!-- clicking on text redirects to the link in quotation marks -->
        <!-- href attribute defines link's destination address-->
        <!-- to link image to another webpage, nest <img> tag inside <a>(anchor) tag-->
        ```
        
        ```html
        i.e.
        <a href="<https://nytimes.com>" target="_blank">The New York Times</a>
        ```
        
        ```html
        <link relationship="stylesheet" type="text/css" href="stylesheet.css">
        <!-- linking to style sheet -->
        ```
        
    -   tables
        
        ```html
        <table>
           <tr>
              <td></td>
              <td></td>
              <td></td>
           </tr>
        </table>
        
        <!-- ^^table w/ one row & three columns -->
        <!-- defined by <table> tag -->
        <!-- divided into table rows w/ <tr> tag -->
        <!-- rows are divided into columns w/ <td> (table data) tag -->
        
        <!-- Table data tags <td> act as data containers within the table.
        They can contain all sorts of HTML elements, such as text, images, lists, other tables, and so on. -->
        
        <table border= "2">
        	<tr>
        		<td>Red</td>
        		<td>Blue</td>
        		<td>Green</td>
        	</tr>
        	<tr>
        		<td> <br /> </td>
        		<td colspan="2"> <br /> </td>
        </table>
        
        <!-- border can be added using border attribute -->
        <!-- table cell can expand using colspan attribute -->
        <!-- can insert any value between starting & closing tag statements -->
        
        <td bgcolor= "red">Red</td>
        <!-- ^^sets background color of table cell to red -->
        <!-- can also use align attribute inside table tag(sepearated from other attributes w/ semicolon(;)) -->
        ```
        
        ```html
        <table style="width:100%">
          <tr>
            <th>Name</th>
            <th colspan="2">Telephone</th>
          </tr>
          <tr>
            <td>Bill Gates</td>
            <td>55577854</td>
            <td>55577855</td>
          </tr>
        </table>
        
        <table style="width:100%">
          <tr>
            <th>Name:</th>
            <td>Bill Gates</td>
          </tr>
          <tr>
            <th rowspan="2">Telephone:</th>
        		<!-- rowspan -->
            <td>55577854</td>
          </tr>
          <tr>
            <td>55577855</td>
          </tr>
        </table>
        ```
        
        ```html
        <h2>Basic HTML Table</h2>
        
        <table style="width:100%">
          <tr>
            <th>Firstname</th>
            <th>Lastname</th> 
            <th>Age</th>
          </tr>
          <tr>
            <td>Jill</td>
            <td>Smith</td>
            <td>50</td>
          </tr>
          <tr>
            <td>Eve</td>
            <td>Jackson</td>
            <td>94</td>
          </tr>
          <tr>
            <td>John</td>
            <td>Doe</td>
            <td>80</td>
          </tr>
        </table>
        
        </body>
        </html>
        ```
        
        ```html
        <!DOCTYPE html>
        <html>
        <head>
        <style>
        table, th, td {
          border: 1px solid black;
        }
        <!-- define table properties(using internal CSS) with class -->
        <!-- 1px = width of border, solid = style of border, black = border color -->
        </style>
        </head>
        <body>
        ```
        
        ```html
        <!-- BORDER STYLES -->
        <!DOCTYPE html>
        <html>
        <head>
        <style>
        p.dotted {border-style: dotted;}
        p.dashed {border-style: dashed;}
        p.solid {border-style: solid;}
        p.double {border-style: double;}
        p.groove {border-style: groove;}
        p.ridge {border-style: ridge;}
        p.inset {border-style: inset;}
        p.outset {border-style: outset;}
        p.none {border-style: none;}
        p.hidden {border-style: hidden;}
        p.mix {border-style: dotted dashed solid double;}
        </style>
        </head>
        <body>
        ```
        
        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a55d7fe3-69f7-4a9d-91c3-4add23cf6944/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a55d7fe3-69f7-4a9d-91c3-4add23cf6944/Untitled.png)
        
        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/308b93c4-2057-4a2d-9e98-bf99c5d62c0f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/308b93c4-2057-4a2d-9e98-bf99c5d62c0f/Untitled.png)
        
        ```html
        <!DOCTYPE html>
        <html>
        <head>
        <style>
        table, th, td {
          border: 1px solid black;
          border-collapse: collapse;
        	<!--for borders to collapse into one, add CSS border-collapse property(makes the borders the same for all of the table)-->
        }
        </style>
        </head>
        <body
        ```
        
        ```html
        <!DOCTYPE html>
        <html>
        <head>
        <style>
        table, th, td {
          border: 1px solid black;
          border-collapse: collapse;
        }
        th, td {
          padding: 15px;
        	<!--cell padding specifies space between cell content and borders, basically same as regular padding -->
        }
        </style>
        </head>
        <body>
        ```
        
    -   blog schedule(contains minor note(s))
        
        ```html
        <!DOCTYPE html>
        <html>
          <head>
          </head>
          <body>
            <h1><span>My Coding Schedule</span></h1>
            <table>
              <tr>
                <th>Day</th>
                <th>Mon</th>
                <th>Tue</th>
                <th>Wed</th>
                <th>Thu</th>
                <th>Fri</th>
              </tr>
        
        <!-- html <th> tag stands for & is table heading -->
        
              <tr>
                <td>8-8:30</td>
                <td class="selected">Learn</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
              </tr>
        
              <tr>
                <td>9-10</td>
                <td></td>
                <td class="selected">Practice</td>
                <td></td>
                <td></td>
                <td></td>
              </tr>
        
              <tr>
                <td>1-1:30</td>
                <td></td>
                <td></td>
                <td class="selected">Play</td>
                <td></td>
                <td></td>
              </tr>
        
              <tr>
                <td>3:45-5</td>
                <td></td>
                <td></td>
                <td></td>
                <td class="selected">Code</td>
                <td></td>
              </tr>
        
              <tr>
                <td>6-6:15</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td class="selected">Discuss</td>
              </tr>
            </table>
          </body>
        </html>
        ```
        
    -   types of elements
        
        ```html
        <!DOCTYPE html>
        <html>
          <head>
          </head>
          <body>
        
        <!-- HTML elements: defined as block level or inline -->
        
        <!-- block level elements start from new line -->
        <!-- <h1>, <form>, <li>, <ol>, <ul>, <p>, <pre>, <table>, <div>, etc. -->
        
        <!-- inline elements normally displayed w/o line breaks -->
        <!-- <b>, <a>, <strong>, <img>, <input>, <em>, <span>, etc. -->
        
            <h1>Headline</h1>
            <div style="background-color:green; color:white; padding:20px;">
              <p>Some paragraph text goes here</p>
              <p>Another paragraph goes here</p>
            </div>
        
        <!-- <div> element: block level. often used as container for other HTML elements: when used w/ CSS styling, <div> element can be used to style blocks of content(like above) -->
        
        		<h2>Some
        			<span style="color:red">Important</span>
        		Message</h2>
        
        <!-- <span> element: inline element. similarly, often used as container for some text. when used together w/ CSS, though, can be used to style only parts of the text(like above) -->
        
        <!--The <div> element defines a block-level section in a document.
        The <span> element defines an inline section in a document. -->
        
        <!-- other elements:
        APPLET - embedded Java applet
        IFRAME - inline frame
        INS - inserted text
        MAP - image map
        OBJECT - embedded object
        SCRIPT - script within an HTML doc -->
        
        <!-- can insert inline elements inside block elements, but not vice versa. i.e. you can have multiple <span> elements inside one <div> element -->
        
          </body>
        </html>
        ```
        
-   Basics: 12/26 & 12/27/2020 - forms
    
    ```html
    <body>
    <!-- forms used to collect information from user -->
    		<form action=""> <!-- action attribute points to a webpage that will load after submission of form -->
    		</form>
    <!-- form usually submitted to a web page on a web server -->
    
    		<form action="url" method="GET">
    		<form action="url" method="POST">
    <!-- method attribute specifies HTTP method(GET or POST) to be used when forms are submitted. When you use GET, the form data will be visible in page address. Use POST if the form is updating data, or includes sensitive info. POST offers better security, since the submitted data is not visible in page address.-->
    <!-- i.e. when you conduct a search in Amazon or Google, it will include the form data in the page address. However, when you enter a password in Google, it isn't included. -->
    </body>
    ```
    
    ```html
    <!-- to take in user input, you need form elements, such as text fields. the <input> element has many variations, depending on type of attribute. can be text, password, radio, URL, submit, etc.-->
    
    <form>
    	<input type="text" name="username" /><br />
    	<input type="password" name="password" />
    </form>
    
    <!-- result: 1 wide rectangle split in half horizontally; one bar has the string "username" nested inside, while the bottom bar has 8 black dots(the string "password"), the way you type in passwords.-->
    
    <!-- name attribute specifies a name for a form -->
    ```
    
    ```html
    <!-- if change input type to radio, allows user to select only one of any number of choices -->
    
    <input type="radio" name="gender" value="male" /> Male <br />
    <input type="radio" name="gender" value="female" /> Female <br />
    
    <!-- result is two lines: first is the circular icon followed by the word "Male" while second is the same except "Female". Can only check off one of the dots -->
    
    <input type="checkbox" name="gender" value="1" /> Male<br />
    <input type="checkbox" name="gender" value="2" /> Female<br />
    
    <!-- result is two lines: first is a checkbox followed by the word "Male" while second is the same except "Female". Can check any number of boxes -->
    
    <!-- input tag has no end tag! -->
    ```
    
    ```html
    <!-- submit button submits a form to action attribute -->
    
    <input type="submit" value="Submit" />
    <!-- result is a grey rectangular button that has the word "Submit" on it -->
    
    <!-- after form is submitted, data should be processed on the server using a programming language, such as PHP(i.e. to check age requirements) -->
    ```
    
    contact form:
    
    ```html
    <h1><span>Contact Me</span></h1>
    <form>
    	<input name="name" type="text" /><br/>
    	<input name="email" type="email" /><br/>
    	<textarea name="message"></textarea>
    	<input type="submit" value="SEND" class="submit" />
    </form>
    ```
    
    -   above is a static HTML page: won't actually submit the form. need to create a server-side code in order to submit real form and process data.
    -   textarea supports multiple lines of input
    
    HTML → CSS → JavaScript(?) → PHP(to learn how to create a server-side code)
    
-   Basics: 12/29/2020 - colors, frames
    
    -   did you know? colors are described in hexadecimal values, or HEX, which is base 16 :O
    -   rep w/ red green blue light, or RGB
    -   hex values written with a # before the value(i.e. #D2E0BF; #000000 is black, #FFFFFF is white)
    -   there are $16^6$ combinations for RGB values!
    
    ```html
    <body bgcolor="#000099">
    <!-- turns the whole background of page into a blue color -->
    <!-- The color attribute specifies the color of the text inside a <font> element. -->
    ```
    
    -   frames
        
        ```html
        <frameset cols="100, 25%, *"></frameset>
        <frameset rows="100, 25%, *"></frameset>
        ```
        
        -   page can be divided into frames using special frame doc
        -   <frame> tag defines 1 specific window/frame within a <frameset>. each frame can have different attributes, such as border, scrolling, ability to resize, etc.
        -   <frameset> element specifies number of rows/columns and how much space the frame covers in pixels or percentage.
        -   NOT SUPPORTED IN HTML 5
        
	```html
        <frame noresize="noresize">
        <!-- noresize specifies that a user can't resize a frame element-->
        <!-- frame content should be defined by using the source(src) attribute-->
        <frameset cols="25%,50%,25%">
           <frame src="a.htm" />
           <frame src="b.htm" />
           <frame src="c.htm" />
           <noframes>Frames not supported!</noframes>
        </frameset>
        <!-- no frames used to view website in browsers that don't support frames when viewing. can include its own body tag & other elements. -->
        ```
        
        inserting a YouTube video:
        
        ```html
        <div class="section">
        	<h1><span>My Media</span></h1>
        	<iframe height="150" width="300" 
        src="<https://www.youtube.com/watch?v=hCKBl-TpRzc>"
        allowfullscreen frameborder="0"></iframe>
        </div>
        ```
        
        -   sections created using <div> tag