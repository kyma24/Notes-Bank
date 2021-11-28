-   box model intro
    
    All HTML elements can be considered as boxes. CSS box model represents design & layout of site - margins, borders, paddings, & content.
    
    properties work in the same order: top → right → bottom → left.
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/657c0ae8-71a8-48f2-aa2e-36f1795c1be4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230110Z&X-Amz-Expires=86400&X-Amz-Signature=0accbb9bd8cbb71f679283ef66d6c8c742fe8ddf095bfd2cffa8980cf0cd497c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    used when talking about design & layout
    
-   more on box models
    
    every element of webpage is a box.
    
    CSS uses box model to determine how big boxes are & how to place them
    
    also used to calculate the actual width & height of HTML elements
    
    -   total width of element
        
        when working w/ boxes, important to understand how the total width of element is calculated.
        
        i.e. the total width of the box w/ paddings would be the sum of width + padding left + padding right
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d937ea93-6148-46f3-b00b-ce3558268171/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230140Z&X-Amz-Expires=86400&X-Amz-Signature=53770de0f12eab14ccceeec88ce73e201e0ee2b03438334b18a9fc158a758f7a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        i.e. total width is sum of left & right margins, left & right borders, left & right paddings, and actual width of content.
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/08bd8f1a-8726-4dea-90cc-35fc71089a16/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230155Z&X-Amz-Expires=86400&X-Amz-Signature=1289f054aceda5d59538ffd506574ccf4ae9ce4a665da05c7c27cca07d51bc8b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        note: When you set the width and height properties of an element with CSS, you set the width and height of the content area. When setting a background-color to a box, it covers the content area, as well as the padding.
        
    -   total height of element
        
        total height is calculated same way as width
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/db555e9c-8a79-48b8-8a45-545d145bacea/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230222Z&X-Amz-Expires=86400&X-Amz-Signature=f82dadc25354b86c71e1d9f6fe0fe79cdfd9b645819f4f83410beba1cc7c98ce&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        To summarize, Total element height = height + top padding + bottom padding + top border + bottom border + top margin + bottom margin
        
-   border properties
    
    CSS border property allows us to customize borders of HTML elements
    
    in order to add a border to element, need to specify **size**, **style**, and **color** of border
    
    ```html
    <p>This is an example of a solid border.</p>
    ```
    
    ```css
    p {
    	padding: 10px;
    	border: 5px solid green;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/31452355-75b1-48e2-8c00-142253d9bf32/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230241Z&X-Amz-Expires=86400&X-Amz-Signature=9af7c45a058097d6fd44aa99109cc06b593c65169480fa76ac4d6ff9f5106e25&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    -   border-width
        
        specifies width of border
        
        ```html
        <p class="first">
            Border width of this paragraph is set to 2px.
        </p>
        <p class="second">
            Border width of this paragraph is set to 5px.
        </p>
        ```
        
        ```css
        p.first {
        	padding: 10px;
        	border-style: solid;
        	border-width: 2px;
        }
        p.second {
        	padding: 10px;
        	border-style: solid;
        	border-width: 5px;
        }
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c1f95e50-c9e3-4bf3-89b7-03b5bbf95c08/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230307Z&X-Amz-Expires=86400&X-Amz-Signature=0c9c86db23c8796b4a1defd0744b66ab43df57a7e3254baed6cdca360f495c1b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
    -   border-color
        
        ```html
        <p class="first">
           Border color has been created using <strong>color name.</strong>
        </p>
        <p class="second">
           Border color has been created using <strong>Hex values.</strong> 
        </p>
        <p class="third">
           Border color has been created using <strong>RGB values.</strong> 
        </p>
        ```
        
        ```css
        p.first {
        	padding: 10px;
        	border-style: solid;
        	border-width: 2px;
        	border-color: blue;
        }
        p.second {
        	padding: 10px;
        	border-style: solid;
        	border-width: 2px;
        	border-color: #FF6600;
        }
        p.third {
        	padding: 10px;
        	border-style: solid;
        	border-width: 2px;
        	border-color: rgb(0,153,0);
        }
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fd01006e-d89e-4fa0-9536-a5a036af8118/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230330Z&X-Amz-Expires=86400&X-Amz-Signature=c9fa459d30d97a826679b1ec86bba360d8998811d444351ce26499ecde3e615b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        note: none of border properties will have any effect unless border-style property is set; determines the style of the border, w/o style will be nothing
        
    -   border-style
        
        default value of border-style is none, which means no border
        
        ```html
        <p class="none">This paragraph has no border.</p>
        <p class="dotted">This is a dotted border.</p>
        <p class="dashed">This is a dashed border.</p>
        <p class="double">This is a double border.</p>
        <p class="groove">This is a grooved border.</p>
        <p class="ridge">This is a ridged border.</p>
        <p class="inset">This is an inset border.</p>
        <p class="outset">This is an outset border.</p>
        <p class="hidden">This is a hidden border.</p>
        ```
        
        ```css
        p.none {border-style: none;}
        p.dotted {border-style: dotted;}
        p.dashed {border-style: dashed;}
        p.double {border-style: double;}
        p.groove {border-style: groove;}
        p.ridge {border-style: ridge;}
        p.inset {border-style: inset;}
        p.outset {border-style: outset;}
        p.hidden {border-style: hidden;}
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/63c28f02-e52a-4fa0-9f9e-7b1431bb5bd9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230351Z&X-Amz-Expires=86400&X-Amz-Signature=e607b4982990ad4fd57361456d958ce1e22203a750ac8aa567ee97631ccf5bba&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        note: In CSS, it is possible to specify different borders for different sides, using the following properties: border-top-style, border-right-style, border-bottom-style, and border-left-style for the corresponding sides.
        
-   CSS width & height
    
    ```html
    <div>The total width and height of this element is 100px.</div>
    ```
    
    ```css
    div {
    	border: 5px solid green;
    	width: 90px;
    	height: 90px;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1cf7361d-f153-41c0-9543-a36d3e75b383/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230413Z&X-Amz-Expires=86400&X-Amz-Signature=b1b9db8ff90e024d8348ea2e6ef72efc4bb3b0a8ab2e9766c5062829859fe645&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    note: The total width and height of the box will be the 90px+5px (border)+5px(border) = 100px;
    
    -   measurement
        
        can be assigned using percents
        
        ```html
        <div>The total width of this element is <strong>100%</strong> and the total height is <strong>100px</strong> .</div>
        ```
        
        ```css
        div {
        	border: 5px solid green;
        	width: 100%;
        	height: 90px;
        }
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/29ecc8a4-ba52-4d7b-b6e3-7483002c124b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230431Z&X-Amz-Expires=86400&X-Amz-Signature=f9daf7fbb73e3f23f1e928b1dc663476366ad4371d0f27f3518af953f5cb0fb9&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        note: usually expressed in pixels & percentages
        
    -   minimum/maximum sizes
        
        can use following properties
        
        **min-width** - the minimum width of an element
        
        **min-height** - the minimum height of an element
        
        **max-width** - the maximum width of an element
        
        **max-height** - the maximum height of an element
        
        ```html
        <p class="first">The <strong>minimum height </strong> of this paragraph is set to 100px.</p>
        <p class="second">The<strong> maximum width </strong> of this paragraph is set to 100px.</p>
        ```
        
        ```css
        p.first {
        	border: 5px solid green;
        	min-height: 100px;
        }
        p.second {
        	border: 5px solid green;
        	max-width: 100px;
        }
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1b50b4a0-5549-4378-b2d8-12400f2a7419/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230450Z&X-Amz-Expires=86400&X-Amz-Signature=23950e616a0c5e3d56d2c3c358b448c1d53e1288955d6272dfeb6dd80c56780e&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)