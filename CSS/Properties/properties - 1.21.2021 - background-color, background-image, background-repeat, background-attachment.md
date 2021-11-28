-   background-color
    
    ```html
    <p>The background color of this page is set to LightSkyBlue.</p>
    ```
    
    ```css
    body {
    	background-color: #87CEFA;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f513185b-dd5e-4904-8876-fda292342ed1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230619Z&X-Amz-Expires=86400&X-Amz-Signature=170cc5a6ea77b1f32bfa62996cbd1e1a51bfc709223e656643fdd70f5845279a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    can use color name, hexadecimal values, & RGB
    
    ```html
    <h1>This is a heading</h1>
    <p> This is a paragraph</p>
    ```
    
    ```css
    body {
    	background-color: #C0C0C0;
    }
    h1 {
    	background-color: rgb(135,206,235);
    }
    p {
    	background-color: LightGreen;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/feeba2e6-4244-4511-824a-fe7c941b4679/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230636Z&X-Amz-Expires=86400&X-Amz-Signature=5d6ba3fa3ade44bc845c9649d38a4a9c44d8e65f2fd3f31557c9a0497e716fd1&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
-   background-image
    
    sets 1 or several background images in an element
    
    ```css
    body {
    	background-image: url("css_logo.png");
    	background-color: #e9e9e9;
    }
    /*url specifies path to image file. both relative & absolute paths are supported*/
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5570e054-87c8-48c4-a39a-8996c9900236/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230653Z&X-Amz-Expires=86400&X-Amz-Signature=63a5c17cb2822712b96caf01a8a151253889c411204d2530ed28962e3cfd6406&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    By default, a background-image is placed at the top-left corner of an element, and is repeated both vertically and horizontally to cover the entire element.
    
    can also do for individual elements:
    
    ```html
    <p>This paragraph has a background image.</p>
    ```
    
    ```css
    p {
    	padding: 30px;
    	background-image: url("green_photo.jpg");
    	color: white;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f71b7f2e-784d-4563-a4f1-655708c112ec/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230715Z&X-Amz-Expires=86400&X-Amz-Signature=39c1c34e48151b10a0782d3eaada568617c94b5f98a1fc764c3a9be3f011a62b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    to specify > 1 image, separate URLs w/ commas
    
-   background-repeat
    
    The background repeat property specifies how background images are repeated. A background image can be repeated along the **horizontal axis**, the **vertical axis**, **both axes**, or **not repeated at all**.
    
    **repeat-x** will repeat background-image only **horizontally**.
    
    ```css
    body {
    	background-image: url("css_logo.png");
    	background-repeat: repeat-x;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5e1f4cbe-ccc1-493e-a2fa-024169458569/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230734Z&X-Amz-Expires=86400&X-Amz-Signature=7d1ecbe64ffd1e52e3d3c2e8827b18a8f3fec26c3c2fafe46dbcb11e57a47ec8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    **repeat-y** will repeat background-image only **vertically**.
    
    ```css
    body {
    	background-image: url("css_logo.png");
    	background-repeat: repeat-y;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1f8491b1-c51f-4b53-a93e-97a1ebae3821/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230748Z&X-Amz-Expires=86400&X-Amz-Signature=bd033ba2461be766cdccb1637e9e4dab882bad62cd4c9d668354d67a398326f2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    If you want the image to be shown only once, use the no-repeat value.
    
    -   setting value to inherit
        
        will take same specified value as property for element's parent
        
        i.e. set body background repeat only horizontally. If we set some paragraph background-repeat values to be inherited, will take the same property value as body element
        
        ```css
        body {
        	background-image: url("css_logo.png");
        	background-repeat: repeat-x;
        }
        p {
        	background-image: url("css_logo.png");
        	background-repeat: inherit;
        	margin-top: 100px;
        	padding: 40px;
        }
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e16f7297-e3a0-4c22-b80f-fa293f7c6526/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230824Z&X-Amz-Expires=86400&X-Amz-Signature=331e8e5a8a5eb1e00f88310b3a2311eeb66de13157df4b09df5417a05f00faa4&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
-   background-attachment
    
    sets whether background image is fixed or scrolls w/ rest of page
    
    even if element has scrolling mechanism, "fixed" background doesn't move w/ element.
    
    ```css
    body {
    	background-image: url("css_logo.png");
    	background-repeat: no-repeat;
    	background-attachment: fixed;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/81bd3996-c84b-484d-a410-f3b4bf2f740a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230841Z&X-Amz-Expires=86400&X-Amz-Signature=d859e3d80cc6433b4b8669abcdc67de45665fd84730bb7bfb0d5d5e549f281c7&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    more values include **inherit** and **scroll**
    
    when background-attachment is set to inherit, will inherit value from parent element.
    
    when set attachment to scroll, background image will scroll w/ rest of content(default)
    
    ```css
    body {
    	background-image: url("css_logo.png");
    	background-repeat: no-repeat;
    	background-attachment: scroll;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/30adff78-fda8-4a5f-a463-2eb20e5d8709/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T230908Z&X-Amz-Expires=86400&X-Amz-Signature=ab226e5b461eac1bd0f06010fcc64ea9dcafc9683557c3f492171c596e653bc7&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)