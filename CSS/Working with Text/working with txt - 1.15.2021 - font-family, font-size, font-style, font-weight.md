-   font-family
    
    2 types of font families addresses:
    
    -   **font family**: a specific font family (like Times New Roman or Arial)
    -   **generic family**: a group of font families with a similar look (like Serif or Monospace)
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1b89161d-7509-4604-87d7-c0be24a826af/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T223457Z&X-Amz-Expires=86400&X-Amz-Signature=decb0baffedfdeafd4290fa654739ea002612e24dced64eebda57909cca095b2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    ```html
    <p class="serif">
       This is a paragraph shown in serif font.
    </p>
    <p class="sansserif">
       This is a paragraph shown in sans-serif font.
    </p> 
    <p class="monospace">
       This is a paragraph shown in monospace font.
    </p> 
    <p class="cursive">
       This is a paragraph shown in cursive font.
    </p> 
    <p class="fantasy">
       This is a paragraph shown in fantasy font.
    </p>
    ```
    
    ```css
    p.serif{
    	font-family: "Times New Roman", Times, serif;
    }
    p.sansserif{
    	font-family: Helvetica, Arial, sans-serif;
    }
    p.monospace{
    	font-family: "Courier New", courier, monospace;
    }
    p.cursive{
    	font-family: Florence, cursive;
    }
    p.fantasy{
    	font-family: Blippo, fantasy;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2895ba28-944d-4fae-becd-3bcbefe270a4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T223652Z&X-Amz-Expires=86400&X-Amz-Signature=747e6cde6f8c0a4e18cfe16888e76a361fc203bd8eaab26e90d73197848d9d5f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    Separate each value with a **comma** to indicate that they are alternatives
    
    If the name of a font family is more than one word, it must be in quotation marks: **"Times New Roman"**
    
    the font-family property should hold some "fallbacks" as alternatives in case something goes wrong. When doing CSS, use more than 1 font to avoid unexpected behaviors. If the client computer somehow doesn't have the font you choose, there will be insurance and it will try the next font. Should also specify generic family if no other fonts are available.
    
    ```css
    body {
       font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
    } 
    ```
    
-   font-size
    
    One way to set the size of fonts on the web is to use keywords. For example xx-small, small, medium, large, larger, etc.
    
    ```html
    <p class="small">
       Paragraph text set to be small
    </p>
    <p class="medium">
       Paragraph text set to be medium
    </p>
    <p class="large">
       Paragraph text set to be large
    </p>
    <p class="xlarge">
       Paragraph text set to be very large
    </p>
    ```
    
    ```css
    p.small {
    	font-size: small;
    }
    p.medium {
    	font-size: medium;
    }
    p.large {
    	font-size: large;
    }
    p.xlarge {
    	font-size: x-large;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9a4d38c0-66ff-45ac-9eb7-cfe26aba7ef9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T223714Z&X-Amz-Expires=86400&X-Amz-Signature=faf5f6a142c2c0f6213a3f58fdf20d4ae98cc5015e174aa46b3070d5f8ab6e5f&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    Keywords are useful if you do not want the user to be able to increase the size of the font because it will adversely affect your site's appearance.
    
    can also use numerical values in pixels or ems to manipulate font size(along w/ percentage)
    
    px gives you accuracy, em is relative → em = pixels/16
    
    ```css
    h1 {
    	font-size: 20px;
    }
    ```
    
    ```css
    /* or... */
    h1 {
    	font-size: 1.25em;
    }
    ```
    
-   font-style
    
    typically used to specify italic text, but has 3 values: normal, _italic_, & _oblique_
    
    oblique is basically the same as italic, but less supported
    
    ```html
    <p class="italic">This is a paragraph in italic style.</p>
    ```
    
    ```css
    p.italic {
    	font-style: italic;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/706ae998-8ccc-40cc-aa48-b5432d92582b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T223736Z&X-Amz-Expires=86400&X-Amz-Signature=24918682003d27520f9e402e41ab539810b8c0a7790cb7f9ae5a4ed5e88dace6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    ```html
    <p class="normal">This paragraph is normal.</p>
    <p class="italic">This paragraph is italic.</p>
    <p class="oblique">This paragraph is oblique.</p>
    ```
    
    ```css
    p.normal {
    	font-style: normal;
    }
    p.italic {
    	font-style: italic;
    }
    p.oblique {
    	font-style: oblique;
    }
    ```
    
    can also use i tag
    
-   font-weight
    
    ctrls font boldness, can be measured in **lighter**, **normal**(default), **bold**, and **bolder**
    
    ```html
    <p class="light">This is a font with a "lighter" weight.</p>
    <p class="bold">This is a font with a "bold" weight.</p>
    <p class="bolder">This is a font with a "bolder" weight.</p>
    ```
    
    ```css
    p.light {
    	font-weight: lighter;
    }
    p.bold {
    	font-weight: bold;
    }
    p.bolder {
    	font-weight: bolder;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2267a4a5-65a6-4f6f-9744-e5bc3b949c4b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T223823Z&X-Amz-Expires=86400&X-Amz-Signature=bc08606bb67decce7d7e90b182c3820b6001b91d59963dec5cfe02ebce3876d8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    font weight can also be measured w/ numbers from 100-900 for thickness
    
    400 = normal, 700 = bold
    
    ```html
    <p class="light">This is a font with a "lighter" weight.</p>
    <p class="thick">This is a font with a "bold" weight.</p>
    <p class="thicker">This is a font with a "700" weight.</p>
    ```
    
    ```css
    p.light {
    	font-weight: lighter;
    }
    p.thick {
    	font-weight: bold;
    }
    p.thicker {
    	font-weight: 700;
    }
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7cebd6fe-5968-4cfe-91b5-2b92a38e45c9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T223836Z&X-Amz-Expires=86400&X-Amz-Signature=59a99c10338d1db84e69bfd4267433c95ad718ef9adb6c5ea210334c4b1ed111&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)