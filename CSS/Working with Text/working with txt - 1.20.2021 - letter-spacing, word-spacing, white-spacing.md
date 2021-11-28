-   letter-spacing
    
    specifies space between characters in text
    
    values:
    
    -   normal - defines default style w/ no extra space btwn characters
    -   length - defines extra space btwn characters using measurement units like px, pt, cm, mm, etc
    -   inherit - inherits property from parent element
    
    ```html
    <!--HTML FILE-->
    <p class="normal">This paragraph has no additional letter-spacing applied.</p>
    <p class="positive ">This paragraph is letter-spaced at 4px.</p>
    ```
    
    ```css
    p.normal {
    	letter-spacing: normal;
    }
    p.positive {
    	letter-spacing: 4px;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0eac38b2-5374-4948-80ab-3c3b3c426bfc/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T225729Z&X-Amz-Expires=86400&X-Amz-Signature=796c7913a9ba903bb02867a74d8be2937188515ef9509f90ae11904ab36fbb39&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    can also use negative values: comparison btwn pos & neg
    
    ```html
    <!--HTML FILE-->
    <p class="positive">This paragraph is letter-spaced at 4px.</p>
    <p class="negative">This paragraph is letter-spaced at -1.5px</p>
    ```
    
    ```css
    p.positive {
    	letter-spacing: 4px
    }
    p.negative {
    	letter-spacing: -1.5px
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fcc45979-db21-4245-9fa2-5b6e32922932/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T225744Z&X-Amz-Expires=86400&X-Amz-Signature=144b9afb53b1c8ef44b2b2029a9f5febc1f4ce0be4138011fe78f907484602a2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
-   word-spacing(& measurement units)
    
    specifies space btwn words in text
    
    has same word-spacing values as letter-spacing: normal, length, & inherit
    
    ```html
    <!--HTML FILE-->
    <p class="normal">This paragraph has no additional word-spacing applied.</p>
    <p class="px">This paragraph is word-spaced at 30px.</p>
    ```
    
    ```css
    p.normal {
    	word-spacing: normal;
    }
    p.px {
    	word-spacing: 30px;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4b7800f3-0961-4e9c-abf8-3afc5607f45e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T225803Z&X-Amz-Expires=86400&X-Amz-Signature=61643286ba409971d665fc4a664b2835c704182ebee21ea64cfd3aa96bfaead9&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    note: When a weird spacing is used, and it is necessary to keep the selected paragraph with normal word spacing, the normal option is usually used.
    
    -   measurement units
        
        can define extra space btwn words with units: px, pt, pc, cm, mm, inches, em, and ex.
        
        negative values will also work.
        
        ```html
        <!--HTML FILE-->
        <p class="positive">This paragraph is word-spaced at 20px.</p>
        <p class="negative">This paragraph is word-spaced at -5px.</p>
        ```
        
        ```css
        p.positive {
        	word-spacing: 20px;
        }
        p.negative {
        	word-spacing: -5px;
        }
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/dc908371-6ce5-401e-9fb2-82c2818a2ca1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T225825Z&X-Amz-Expires=86400&X-Amz-Signature=d6a354fd7d694e60bc06425b6cb2b7d7bbec5554f716ddc39c7a9da9d78ecd27&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
-   white-spacing
    
    this property specifies how a blank space inside element should be handled
    
    can be set as normal, inherit, nowrap, and more
    
    The nowrap value makes the text continue on the same line until a <br> tag is encountered, and also collapses all sequences of whitespace into a single whitespace
    
    ```html
    <!--HTML FILE-->
    <p>
    This paragraph has         multiple spaces      and
    a line break, but it will be ignored, as we used the nowrap value. 
    </p>
    ```
    
    ```css
    /*CSS FILE*/
    p {
    	white-space: nowrap;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/dc908371-6ce5-401e-9fb2-82c2818a2ca1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T225825Z&X-Amz-Expires=86400&X-Amz-Signature=d6a354fd7d694e60bc06425b6cb2b7d7bbec5554f716ddc39c7a9da9d78ecd27&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    some more white-space values:
    
    **pre** - text will only wrap on line breaks and white space
    
    **pre-line** - text will wrap where there is a break in code, but extra white space is still ignored
    
    **pre-wrap** - text will wrap when necessary, and on line breaks
    
    ```html
    <!--HTML FILE-->
    <p class="pre"> 
    In the markup we have multiple            spaces 
    and a line break. 
    </p>
    <p class="preline"> 
    In the markup we have multiple            spaces 
    and a line break, but in the result multiple spaces are ignored. 
    </p>
    <p class="prewrap"> 
    In the markup we have              multiple 
    spaces and a line break.
    </p>
    ```
    
    ```css
    /*CSS FILE*/
    p.pre {
    	white-space: pre;
    }
    p.preline {
    	white-space: pre-line;
    }
    p.prewrap {
    	white-space: pre-wrap;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6d9d62fd-fa1d-400c-a475-09b724dfad14/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T225839Z&X-Amz-Expires=86400&X-Amz-Signature=66dc98cca65ee2cd3644f631adc33c0d4a439b2c7a91fa5b61a61998907142f0&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    note: Pre-wrap value behaves as the pre value, except that it adds extra line breaks to prevent the text breaking out of the element's box.