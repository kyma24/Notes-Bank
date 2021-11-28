-   audio
    
    ```html
    <!--audio element specifies standard for embedding audio in a webpage-->
    
    <!--two different ways to specify audio source file's URL: first is source attribute-->
    <audio src="audio.mp3" controls>
    	Audio element not supported by your browser
    </audio>
    
    <!--second uses <source> element inside <audio> element -->
    <audio controls>
    	<source src="audio.mp3" type="audio/mpeg">
    	<source src="audio.ogg" type="audio/ogg">
    
    <!-- multiple <source> elements can be linked to different audio files. Browser will use first recognized format -->
    ```
    
    ```html
    <audio controls>
    	<source src="audio.mp3" type="audio/mpeg">
    	<source src-"audio.ogg" type="audio/ogg">
    	Audio element not supported by your browser.
    </audio>
    ```
    
    `The text between the <audio> and </audio> tags will display in browsers that do not support the <audio> element`
    
   ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ccca9be9-372d-4e2f-bcad-241da5834ef7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T220739Z&X-Amz-Expires=86400&X-Amz-Signature=9429750942efdb7e180ed868bb08032e5d2a86593331fce7fa469660bb176386&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    ```html
    attributes of <audio>:
    
    controls
    - specifies that audio controls should be displayed(such as a play/pause button, etc.)
    
    autoplay
    - when this attribute is defined, audio starts playing as soon as its ready w/o asking for visitor's permission
    <audio controls autoplay>
    
    loop
    - this attribute is used to have audio replay every time it's finished
    <audio controls autoplay loop>
    
    many others, including source
    
    <!-- currently there are 3 supported file formats for <audio> element: MP3, WAV, and OGG -->
    ```
    
-   video
    
    `video element very similar to audio element`
    
    `can specify video source URL using an attribute in video element, or source elements inside video element:`
    
    ```html
    <video controls>
    	<source src="video.mp4" type="video/mp4">
    	<source src="video.ogg" type="video/ogg">
    	Video is not supported by your browser
    </video>
    ```
    
    `another aspect that audio & video elements have in common is that major browsers don't all support same file types. If browser doesn't support first video type, it will try next one.`
    
    `again, another aspect shared by both audio and video elements is that each has controls, autoplay and loop attributes`
    
    `the following code will make the video replay after it finishes playing:`
    
    ```html
    <video controls autoplay loop>
    	<source src="video.mp4" type="video/mp4">
    	<source src="video.ogg" type="video/ogg">
    	Video is not supported by your browser
    </video>
    ```
    
    `the 3 supported video formats of video element is MP4, WebM, and OGG`
    
-   progress bar
    
    `<progress> element provides ability to create progress bars on a website. can be used within headings, paragraphs, or anywhere else in the body`
    
    **Progress Element Attributes**
    
    **Value:** Specifies how much of the task has been completed
    
    **Max:** Specifies how much work the task requires in total
    
    ```html
    Status: <progress min="0" max="100" value="35">
    </progress>
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9af9b841-b19d-4cb5-9c2d-320029cb7b2c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210307T220801Z&X-Amz-Expires=86400&X-Amz-Signature=0b27e899c907a3ecf84358191eae8487ce9f3bfa50238ff605da8bd2794c63f5&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    -   use progress tag in conjunction w/ JavaScript to dynamically display a task's progress!
    <progress>