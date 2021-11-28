-   basics: 1/14/2021 - intro, types of CSS
    
    -   intro
        
        CSS stands for **C**ascading **S**tyle **S**heets.
        
        -   **Cascading** refers to the way CSS applies one style on top of another.
        -   **Style Sheets** control the look and feel of web documents.
        
        **CSS** and **HTML** work hand in hand:
        
        -   HTML sorts out the page structure.
        -   CSS defines how HTML elements are displayed.
        
        CSS allows you to apply specific styles to specific HTML elements.
        
        The main benefit of CSS is that it allows you to separate **style** from **content**.
        
        Using just HTML, all the styles and formatting are in the same place, which becomes rather difficult to maintain as the page grows.
        
        Yes, you should do(very much recommended) external CSS & HTML.
        
    -   inline, internal, & external CSS
        
        -   for inline, use style attribute inside a block level element
        
        ```html
        <h1 style="font-size:200%; font-family:arial; color:#000000; background-color:black;">
        	This is a header.
        </h1>
        ```
        
        -   for embedded or internal, put style element inside the head section(internal style sheet may be used if one single page has a unique style)
        
        ```html
        <html>
        	<head>
        		<style>
        			p{
        				background-color:black;
        				color:white;
        				font-family:tahoma;
        				}
        		</style>
        	</head>
        	<body>
        		<p>this is a paragraph</p>
        		<p> this is also a paragraph</p>
        	</body>
        </html>
        <!--now all paragraphs have a black background in white text w/ the serif font Tahoma-->
        ```
        
        -   for external, create another file in the same location the HTML file is stored in. Take the embedded CSS style part and copy paste it to the new sheet. After that, get rid of the style starting & closing tags, then paste in link rel="stylesheet" href="example.css", and it will work the same(can also put classes into the external CSS style sheet)
        
        ```html
        <head>
           <link rel="stylesheet" href="example.css">
        	<!--remember to save as .css for the CSS external file, and .html for the HTML external flie-->
        </head>
        <body>
           <p>This is my first paragraph.</p>
           <p>This is my second paragraph. </p>
           <p>This is my third paragraph. </p>
        </body>
        ```
        
        remember: style attribute can contain any CSS property
        
        Both relative and absolute paths can be used to define the href for the CSS file. In our example, the path is relative, as the CSS file is in the same directory as the HTML file.
        
-   basics: 1/15/2021 - CSS rules & selectors, style cascade & inheritance
    
    -   css syntax
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c78e1391-baa9-479d-84fe-a50e75963d22/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T222932Z&X-Amz-Expires=86400&X-Amz-Signature=2e70c48ab494fb0cf9d7fa05a55c5221b82926225efcb18d235c74ba8d4c5b98&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        The selector points to the HTML element you want to style.
        
        The declaration block contains one or more declarations, separated by semicolons.
        
        Each declaration includes a property name and a value, separated by a colon.
        
        -   reference 1/4/2021 folder > anatomy of HTML statement for more
    -   type selectors
        
        -   targets all selectors on page
        
        ```css
        p {
        	color: red;
        	font-size: 130%;
        }
        ```
        
        A CSS declaration always ends with a semicolon, and declaration groups are surrounded by curly braces.
        
    -   id & class selectors
        
        id selectors allow you to style an HTML element that has an id attribute, regardless of their position in the document tree. Here is an example of an id selector:
        
        ```html
        <!--HTML FILE-->
        <div id="intro">
           <p> This paragraph is in the intro section.</p>
        </div>
        <p> This paragraph is not in the intro section.</p>
        ```
        
        ```css
        /*CSS FILE*/
        #intro {
        	color:white;
        	background-color:gray;
        }
        ```
        
        -   to define an id, do hashtag symbol and then the name of the id
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/57c34b5e-abd7-4146-b6d1-c9386dbcba96/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T222958Z&X-Amz-Expires=86400&X-Amz-Signature=13fc8ea925717256e3905b7f1afdd1483acb5900bb23d11fa005ea6f7a6f8a8b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        note: ids can only be used once per page, but classes can be used however many times needed
        
        ```html
        <!--HTML FILE-->
        <div>
           <p class="first">This is a paragraph</p>
           <p> This is the second paragraph. </p>
        </div>
        <p class="first"> This is not in the intro section</p>
        <p> The second paragraph is not in the intro section. </p>
        ```
        
        ```css
        /*CSS FILE*/
        .first {
        	font-size: 200%
        }
        ```
        
        note: To select elements with a specific class, use a period character, followed by the name of the class. Do **NOT** start a class or id name with a number!
        
    -   descendant selectors
        
        descendant selectors are used to select elements that are descendants of another element. When selecting levels, you can select as many levels deep as you need to.
        
        For example, to target only em elements in intro section:
        
        ```html
        <div id="intro">
           <p class="first">This is a <em> paragraph.</em></p>
           <p> This is the second paragraph. </p>
        </div>
        <p class="first"> This is not in the intro section.</p>
        <p> The second paragraph is not in the intro section. </p>
        ```
        
        ```css
        #intro .first em {
        	color:pink;
        	background-color:gray;
        }
        ```
        
        only selected element(in this case, i) will be affected
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d3326b9c-b971-43d8-9a64-b856da97d908/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T223035Z&X-Amz-Expires=86400&X-Amz-Signature=9e61fa59ee87ad2a68e926e248e784df0393920194a08e9174fce587d4380a63&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        The descendant selector matches all elements that are descendants of a specified element.
        
        more on this: [](https://www.w3schools.com/css/css_combinators.asp)[https://www.w3schools.com/css/css\_combinators.asp](https://www.w3schools.com/css/css_combinators.asp)
        
    -   style cascade & inheritance
        
        3 sources of info that form a cascade:
        
        -   The stylesheet created by the **author of the page**
        -   The **browser's default styles**
        -   Styles specified **by the user**
        
        CSS → cascading style sheets
        
        inheritance: how the style is throughout the page. a "child" element(nested) will "inherit" the properties of "parent" element unless stated otherwise
        
        ```html
        <html>
           <head>
              <style>
              body {
                 color: green;
                 font-family: Arial;
              }
             </style>
           </head>
           <body>       
              <p>
              This is a text inside the paragraph. 
              </p>
           </body>
        </html>
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/11fb702e-38d4-4ad6-a4a9-b58ce04a133e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T223054Z&X-Amz-Expires=86400&X-Amz-Signature=408a028e6d5446ac122e3cbaddbcca5bbfcf6d52eb06383d6b9a653f88fe7b95&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        Since the paragraph tag (child element) is inside the body tag (parent element), it takes on any styles assigned to the body tag.