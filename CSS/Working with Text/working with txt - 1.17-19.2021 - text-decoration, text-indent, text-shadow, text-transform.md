-   text-decoration
    
    specifies how text can be decorated
    
    commonly used values:
    
    **none** - The default value, this defines a normal text
    
    **inherit** - Inherits this property from its parent element
    
    **overline** - Draws a horizontal line above the text
    
    **underline** - Draws a horizontal line below the text
    
    **line-through** - draws a horizontal line through the text (substitutes the HTML **s** tag)
    
    i.e.
    
    ```html
    <!--HTML FILE-->
    <p class="none">This is default style of the text (none).</p>
    <p class="inherit">This text inherits the decoration of the parent.</p>
    <p class="overline">This is overlined text.</p>
    <p class="underline">This is underlined text.</p>
    <p class="line-through">This is lined-through text.</p>
    ```
    
    ```css
    /*CSS FILE*/
    p.none {
    	text-decoration: none;
    }
    p.inherit {
    	text-decoration: inherit;
    }
    p.overline {
    	text-decoration: overline;
    }
    p.underline {
    	text-decoration: underline;
    }
    p.line-through {
    	text-decoration: line-through;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/209818ee-ec1b-4763-a777-b71cac92b06e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T225053Z&X-Amz-Expires=86400&X-Amz-Signature=825c55f1e475df1aa5ffa1ac954fab8b52ed19d4b64b144b47fb77c0d2a8210b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    note: can combine the underline, overline, or line-through values in space-separated list to add mult décor lines
    
    another value is **blink**. it makes the text blink, though most browsers ignore this.
    
    ```css
    text-decoration: blink;
    ```
    
-   text-indent
    
    specifies how much horizontal space there should be before the start of (usually) a paragraph/**first line** of text
    
    values are length (px, pt, cm, em, etc.), %, and inherit.
    
    ```html
    <!--HTML FILE-->
    <p>This is an example of 
    <strong>text-indent </strong> property. 
    First line of our text is indented to the right in 60px. 
    Besides pixels you can also use other measurement units, 
    like pt, cm, em, etc. </p>
    ```
    
    ```css
    /*CSS FILE*/
    p {
    	text-indent: 60px;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/24b72efd-4edc-4d03-8d7e-393f58ab1148/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T225123Z&X-Amz-Expires=86400&X-Amz-Signature=0dd0ac95267b6d02ea9fa7e206ec2e820ddb6443ba844e8ea9e699d20af3026a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    negative values are allowed, just will be indented to the left
    
-   text-shadow
    
    adds shadow to text
    
    takes 4 values: 1st defines the distance of the shadow in the x (horizontal) direction, 2nd sets the distance in the y (vertical) direction, 3rd defines the blur of the shadow, 4th sets the color
    
    i.e.
    
    ```html
    <h1>Text-shadow example</h1>
    ```
    
    ```css
    h1 {
    	color: blue;
    	font-size: 30pt;
    	text-shadow: 5px 2px 4px grey;
    }
    ```
    
    **5px** – the X-coordinate
    
    **2px** – the Y-coordinate
    
    **4px** – the blur radius
    
    **grey** – the color of the shadow
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ce8686e0-a748-4a0e-a500-99aa12463727/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T225144Z&X-Amz-Expires=86400&X-Amz-Signature=d2585ff037f295cb027ee7859a6926ae6bc88efbd8fe39e46157b9b5594d1c7f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    if want to add more than 1 shadow, separate shadows w/ list
    
    can also add blur effect to shadow
    
    i.e.
    
    blue drop-shadow, two pixels higher than the main text, one pixel to the left of it, and with a 0.5em blur:
    
    ```html
    <h1>Text-shadow with blur effect</h1>
    ```
    
    ```css
    h1 {
    	font-size: 20pt;
    	text-shadow: rgba(0,0,255,1) -1px -2px 0.5em;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/20cf4c76-19ab-4301-8b2d-46d3d4daaa29/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T225155Z&X-Amz-Expires=86400&X-Amz-Signature=ef6956ea9d3ebf72901d46e2fe07c84d3283481c987ee9322d107131d4a5b4b8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    note: older browsers may not support this
    
-   text-transform
    
    specifies how to capitalize element's text
    
    can make text appear w/ each word capitalized:
    
    ```html
    <!--HTML FILE-->
    <p class="capitalize">
        The value capitalize transforms the first 
        character in each word to uppercase; 
        all other characters remain unaffected.
    </p>
    ```
    
    ```css
    /*CSS FILE*/
    p.capitalize {
    	text-transform: capitalize;
    {
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c244877c-92ee-4743-8ca5-698c8ada2481/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T225215Z&X-Amz-Expires=86400&X-Amz-Signature=8a2d01f44913574d983a7ec42755280ae34d4c482c864ff6f1073b2630e90b9e&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    you can also turn ALL characters in to UPPERCASE or lowercase.
    
    ```html
    <!--HTML FILE-->
    <p class="uppercase">This value transforms all characters to uppercase.</p>
    <p class="lowercase">This value transforms all characters to lowercase.</p>
    ```
    
    ```css
    /*CSS FILE*/
    p.uppercase {
    	text-transform: uppercase;
    }
    p.lowercase {
    	text-transform: lowercase;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a1c77512-53ba-4ff1-a045-7a6fc813df01/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T225228Z&X-Amz-Expires=86400&X-Amz-Signature=07f9a3a170818d49dc1936f5ea3f2879c10650c2a4eda557f9ecb27507de48aa&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    note: value _none_ will produce no capitalization effect(basically default)