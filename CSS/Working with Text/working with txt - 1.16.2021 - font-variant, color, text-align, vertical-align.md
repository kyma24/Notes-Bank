-   font variant
    
    allows font to be converted into small capitals
    
    note: not all browsers support this
    
    values can be set to **normal**, **small-caps**, and **inherit**
    
    ```html
    <p class="normal">Paragraph font variant set to normal.</p>
    <p class="small">Paragraph font variant set to small-caps.</p>
    ```
    
    ```css
    p.normal {
    	font-variant: normal;
    }
    p.small {
    	font-variant: small-caps;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/89aba554-ea9c-474b-87cd-b6058e1417f1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T224727Z&X-Amz-Expires=86400&X-Amz-Signature=6675f922bf4efd40cb34a2db18a43908b2e51d1afd335fb5a5d4a6bfa16c75a8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
-   color
    
    ```html
    <p class="example">The text inside the paragraph is green.</p>
    The text outside the paragraph is black (by default).
    ```
    
    ```css
    /*using color name*/
    p.example {
    	color: green;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a59b4d87-9275-4f2b-bad9-2b8abc640e67/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T224801Z&X-Amz-Expires=86400&X-Amz-Signature=7cb40a5c24b3e559bc4c640c9639ae3110b5baba40000cca1dfc2f2594f39fc9&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    ```html
    <h1>This is a heading</h1>
    <p class="example">This is a paragraph</p>
    ```
    
    ```css
    /*using hexidecimals & RGB*/
    h1 {
    	color: #0000FF;
    }
    p.example {
    	color: rgb(255, 0, 0);
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fb9fe920-5342-47b3-9a39-08d3330b9922/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T224813Z&X-Amz-Expires=86400&X-Amz-Signature=856fbe5187a923e6889d74c84f636b8fdcfe84de1833ed00ce37e556e97b2030&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
-   horizontal text align(text-align)
    
    properties: **left**, **center**, **right**, & **justify**
    
    ```html
    <p class="left">This paragraph is aligned to <strong>left.</strong></p>
    <p class="right">This paragraph is aligned to <strong>right.</strong></p>
    <p class="center">This paragraph is aligned to <strong>center.</strong></p>
    ```
    
    ```css
    p.left {
    	text-align: left;
    }
    p.right {
    	text-align: right;
    }
    p.center {
    	text-align: center;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/02c78c45-5ee5-41b5-8f51-391d748c54c5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T224840Z&X-Amz-Expires=86400&X-Amz-Signature=992f3cafa3eb99e6c416c85b11e6dfb54e8649f1b706310d99969e3dd176834f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    note: when using justify, lines are stretched to provide equal width w/ straight margins like in newspapers
    
-   vertical text align(vertical-align)
    
    vertical alignment values: **top**, **middle**, & **bottom**
    
    ```html
    <!-- for alignment in a table: HTML FILE -->
    <table border="1" cellpadding="2" cellspacing="0" style="height: 150px;">
      <tr>
         <td class="top">Top</td>
         <td class="middle">Middle</td>
         <td class="bottom">Bottom</td>
      </tr>
    </table>
    ```
    
    ```css
    /*CSS FILE*/
    td.top {
    	vertical-align: top;
    }
    td.middle {
    	vertical-align: middle;
    }
    td.bottom {
    	vertical-align: bottom;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/36f3d421-ca0e-4dbb-b31f-5f7909d56a59/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T224905Z&X-Amz-Expires=86400&X-Amz-Signature=1ac06a569cd8be9f6eb3e8839f46b116c523864c05f2aa5dead8c68e187cafdc&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    vertical-align can also take values **baseline**, **sub**, **super**, **%**, or **px**(or pt, cm) ← instead of pixel, can do point or centimeters units
    
    i.e.
    
    ```html
    <!--HTML FILE-->
    <p>This is an <span class="baseline">inline text</span> example.</p>
    <p>This is a <span class="sub">sub line text</span> example.</p>
    <p> This is a <span class="super">super line text</span> example.</p>
    <p> This is a <span class="pixel">pixel</span> example.</p>
    ```
    
    ```css
    /*CSS FILE*/
    span.baseline {
    	vertical-align: baseline;
    }
    span.sub {
    	vertical-align: sub;
    }
    span.super {
    	vertical-align: super;
    }
    span.pixel {
    	vertical-align: -10px;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/36f3d421-ca0e-4dbb-b31f-5f7909d56a59/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T224905Z&X-Amz-Expires=86400&X-Amz-Signature=1ac06a569cd8be9f6eb3e8839f46b116c523864c05f2aa5dead8c68e187cafdc&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    not all elements act the same way for vertical align: additional CSS is needed for div elements
    
    ```html
    <!--HTML FILE-->
    <div class="main">
       <div class="paragraph">
       This text is aligned to the middle
       </div>
    </div>
    ```
    
    ```css
    /*CSS FILE*/
    .main {
    	height: 150px; width: 400px;
    	background-color: LightSkyBlue;
    	display: inline-table;
    }
    .paragraph{
    	display: table-cell;
    	vertical-align: middle;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/57a7e527-871c-4e9d-ba34-5ad600e585e2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T224935Z&X-Amz-Expires=86400&X-Amz-Signature=93319a9c05b7bc4cb5b070fab366549491f2c9b738919933ddab6b8f41d9f7ed&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    note: **display: inline-table;** and **display: table-cell;** styling rules are applied to make the vertical-align property work with divs.