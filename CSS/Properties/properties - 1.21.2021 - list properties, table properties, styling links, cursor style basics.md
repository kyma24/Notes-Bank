-   list-style-type & others
    
    list-style-type: allows us to set different list item markers: in HTML, there are 2 types of lists:
    
    **unordered lists**(ul) - marked w/ bullet points
    
    **ordered lists**(ol) - marked w/ numbers or letters
    
    w/ css, lists can be styled further & images can be used as list item marker
    
    One of the ways is to use the **list-style-type** property, which can be set to **circle**, **square**, **decimal**, **disc**, **lower-alpha**, etc.
    
    ```html
    <ol class="lower-alpha">
       <li>Red</li>
       <li>Green</li>
       <li>Blue</li>
    </ol>
    <ul class="circle">
       <li>Red</li>
       <li>Green</li>
       <li>Blue</li>
    </ul>
    <ul class="square">
       <li>Red</li>
       <li>Green</li>
       <li>Blue</li>
    </ul>
    ```
    
    ```css
    ol.lower-alpha {
    	list-style-type: lower-alpha;
    }
    ul.circle {
    	list-style-type: circle;
    }
    ul.square {
    	list-style-type: square;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/80de0320-0b96-4a31-8d0b-a39ff3fbb098/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T231035Z&X-Amz-Expires=86400&X-Amz-Signature=a9c06f8acc8688f2f89a94c0101ba9a915a5a3db11b951df442892cadbed4534&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    Some of the values are for unordered lists, and some for ordered lists.
    
    -   list image & position
        
        other list properties:
        
        **list-style-image** - specifies an image to be used as the list item marker.
        
        **list-style-position** - specifies the position of the marker box (inside, outside).
        
        ```html
        <p>The following list has list-style-position: <strong>inside</strong>.</p>
        <ul>
           <li>Red</li>
           <li>Green</li>
           <li>Blue</li>
        </ul>
        ```
        
        ```css
        ul {
        	list-style-image: url("logo.jpg");
        	list-style-position: inside;
        }
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/811da9e9-0b0b-495a-a987-5ec758da3f44/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T231129Z&X-Amz-Expires=86400&X-Amz-Signature=9b429fd64b04a797594d938e43036b72da94c46648e43eb4fa6c005a043e29a5&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        "list-style-position: outside" is the default value.
        
    -   list-style
        
        shorthand property for setting list-style-type, list-style-image & list-style-position. Used to set all of the list properties in 1 declaration:
        
        ```css
        ul {
           list-style: square outside none;
        }
        
        /*is the same as*/
        
        ul {
        	list-style-type: square;
        	list-style-position: outside;
        	list-style-image: none;
        }
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d3164a91-e628-4064-b160-d96483019619/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T231155Z&X-Amz-Expires=86400&X-Amz-Signature=295f7f02fb998eba144a6671313349f709d31405b154a6fda4c561e52fec9500&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        note: if one of the property values are missing, the default value for the missing property will be inserted, if any.
        
-   table properties
    
    -   **border-collapse**: specifies whether table borders are collapsed into single border or separated as default. **border-spacing**: if borders are separate, this can be used to change spacing
        
        ```html
        <table border="1">
           <tr>
             <td>Red</td>
             <td>Green</td>
           </tr>
           <tr>
              <td>Blue</td>
              <td>Yellow</td>
           </tr>
        </table>
        ```
        
        ```css
        table {
        	border-collapse: separate;
        	border-spacing: 20px 40px;
        }
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/53a63693-7e84-4965-816b-e01db79a1ca6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T231231Z&X-Amz-Expires=86400&X-Amz-Signature=56a93a680e47e8ea139fe2bcb09f80c017fb9aefcacd1041fee7629ad99cf37a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
    -   **caption-side**: specifies position of table caption. values: **top** or **bottom**
        
        ```html
        <table border="1">
        <caption>Some of Our Courses</caption>
        <tr>
          <th>Course name</th>
          <th>Lessons</th>
          <th>Quizzes</th>
        </tr>
        <tr>
          <td>C++</td>
          <td>81</td>
          <td>363</td>
        </tr>
        <tr>
          <td>JavaScript</td>
          <td>48</td>
          <td>144</td>
        </tr>
        <tr>
          <td>HTML</td>
          <td>38</td>
          <td>119</td>
        </tr>
        <tr>
          <td>CSS</td>
          <td>70</td>
          <td>174</td>
        </tr>
        </table>
        ```
        
        ```css
        caption {
        	caption-side: top;
        }
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ac68cdaf-4a6d-4df0-b156-dfd8eaa2ccca/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T231358Z&X-Amz-Expires=86400&X-Amz-Signature=0f98b6214d258892708e64f7d64b7e88c83f02bb51db6e0edd8965665558872a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
    -   **empty-cells**: specifies whether or not to display borders & background on empty cells in a table. values: **show** or **hide**
        
        ```html
        <table border="1">
          <tr>
            <td>HTML</td>
            <td>CSS</td>
          </tr>
          <tr>
            <td>JavaScript</td>
            <td></td>
          </tr>
        </table>
        ```
        
        ```css
        table {
        	border-collapse: separate;
        	empty-cells: hide;
        }
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/453df0c9-4412-413e-a4c5-9de0de1480f6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T231417Z&X-Amz-Expires=86400&X-Amz-Signature=9f44288dfb713d3d65eb62be48ca41b7d3980a62659afe3548c50dc0109a66e8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
    -   **table-layout**: specifies how width of table columns is calculated.
        
        values:
        
        **auto** - when column or cell width are not explicitly set, the column width will be in proportion to the amount of content in the cells that make up the column → default
        
        **fixed** - when column or cell width are not explicitly set, the column width will not be affected by the amount of content in the cells that make up the column.
        
        ```html
        <p>Table-layout is set to <strong>auto</strong></p>
        <table class="auto">
          <tr>
            <td width="10%">500.000.000.000.000</td>
            <td width="90%">20.000</td>
          </tr>
        </table>
        
        <p>Table-layout is set to <strong>fixed</strong></p>
        <table class="fixed">
          <tr>
            <td width="10%">500.000.000.000.000</td>
            <td width="90%">20.000</td>
          </tr>
        </table>
        ```
        
        ```css
        table {
        	border-collapse: separate;
        	width: 100%;
        	border: 1px solid gray;
        }
        td {
        	border: 1px solid gray;
        }
        table.auto {
        	table-layout: auto;
        }
        table.fixed {
        	table-layout: fixed;
        }
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/63613bd1-e8c9-4b82-8e7c-39465b02a00f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T231442Z&X-Amz-Expires=86400&X-Amz-Signature=e7ff9b831edeb5e068afee923218493bdb0ae27db8debb83e4f87f409a737adb&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
-   styling links
    
    links can be styled differently, depending on what state they are in. The following pseudo selectors are available:
    
    **a:link** - defines the style for normal unvisited links
    
    **a:visited** - defines the style for visited links
    
    **a:active** - a link becomes active once you click on it
    
    **a:hover** - a link is hovered when the mouse is over it
    
    ```html
    <p><a href="<http://www.sololearn.com>" target="_blank">
       This link is hovered when we mouse over it
    </a></p>
    ```
    
    ```css
    a:hover {
    	color: red;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9e2cd708-6177-443d-a125-6e14d386379a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T231525Z&X-Amz-Expires=86400&X-Amz-Signature=da157feb6518db571283acfde66ff2cdb5f8261d22e58dfb28d71b7779f42d68&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/df3b8697-bd5e-48a8-8450-a256559ce050/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T231704Z&X-Amz-Expires=86400&X-Amz-Signature=6450b2bf21240f1774dcd207fbb9acaa5b39f29edceed999215114233cdf480c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    When setting style for several link states, have some order rules:
    
    -   a:hover MUST come after a:link and a:visited
    -   a:active MUST come after a:hover
    
    default: text links underlined by browser
    
    common uses of CSS w/ links is to remove underline.
    
    ```html
    <p><a href="<http://www.sololearn.com>" target="_blank">
       This link has no underline.
    </a></p>
    ```
    
    ```css
    a:link {
    	text-decoration: none;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1f31ff4e-d072-4a95-afd4-5d393fd90d23/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T231912Z&X-Amz-Expires=86400&X-Amz-Signature=846992b907d7205dbf3498771a9a0b33dacc8e959296daf2acdcb727e94a139e&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    some other properties to ctrl look & feel of links
    
    **border:none** - removes border from images with links
    
    **outline:none** - removes the dotted border on clicked lines in IE
    
-   customizing mouse cursor
    
    CSS allows to set desired cursor style when you mouse over element. i.e. you can change cursor into hand icon, help icon, & much more rather than using default pointer.
    
    mouse pointer is set to a help icon when we mouse over span element
    
    ```html
    <span style="cursor:help;">
    	Do you need help?
    </span>
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/74942346-17d7-42c2-8d89-d98ea5c5cb6d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T231942Z&X-Amz-Expires=86400&X-Amz-Signature=e8705e2a09a14b97d34345ddcaac00d96687d1a14e0bacb33a6775cb00b4f7ea&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    numerous other possible values for cursor property
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c97a811b-3227-4add-97aa-150131289874/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T231957Z&X-Amz-Expires=86400&X-Amz-Signature=922265c12624883cf2d0caf3b2456892ae31dd3b48706160ecb7a9aee6e3bb4f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    be careful abt which cursor you choose: if mouse cursor is altered it can also be misleading.
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ca23ee71-4be8-4c73-bc61-8b02e9bce6dc/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T232009Z&X-Amz-Expires=86400&X-Amz-Signature=d7d9d89910e8acf6675d48645265345c95fb4a24893b52b457d858028ac91368&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)