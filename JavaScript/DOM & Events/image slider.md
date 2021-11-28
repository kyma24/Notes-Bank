-   image slider
    
    now can create a sample image slider project. The images will be changed using "Next" and "Prev" buttons.
    
    Now, create the HTML, which includes an image and the two navigation buttons:
    
    ```html
    <div>
    	<button> Prev </button>
    	<img id="slider"
    src="<http://www.sololearn.com/uploads/slider/1.jpg>"
    	width="200px" height="100px" />
    	<button> Next </button>
    ```
    
    now, define sample images in an array:
    
    ```jsx
    var images = [
    	"<http://www.sololearn.com/uploads/slider/1.jpg>",
    	"<http://www.sololearn.com/uploads/slider/2.jpg>",
    	"<http://www.sololearn.com/uploads/slider/3.jpg>"
    ];
    ```
    
    now need to handle the Next and Prev button clicks and call the corresponding functions to change the image.
    
    ```html
    <!-- html -->
    <div>
    	<button onclick="prev()"> Prev </button>
    	<img id="slider"
    src="<http://www.sololearn.com/uploads/slider/1.jpg>"
    	width="200px" height="100px" />
    	<button onclick="next()"> Next </button>
    </div>
    ```
    
    ```jsx
    /* js */
    var images = [
    	"<http://www.sololearn.com/uploads/slider/1.jpg>",
    	"<http://www.sololearn.com/uploads/slider/2.jpg>",
    	"<http://www.sololearn.com/uploads/slider/2.jpg>"
    ];
    var num = 0;
    
    function next() {
    	var slider = document.getElementById("slider");
    	num++;
    	if(num >= images.length) {
    		num = 0;
    	}
    	slider.src = images[num];
    }
    
    function prev() {
    	var slider = document.getElementById("slider");
    	num--;
    	if (num < 0) {
    		num = images.length-1;
    	}
    	slider.src = images[num];
    }
    ```
    
    the num variable holds the current image. The next and previous button clicks are handled by their corresponding functions, which change the source of the image to the next/previous image in the array.
    
    ```html
    <!-- i.e. content of paragraph after user clicks on it twice would be 5 -->
    <p id='txt' onclick='test();'>20</p>
    <script>
    function test() {
      var x=document.getElementById('txt');
      var n = x.innerHTML;
      x.innerHTML = n/2;
    }
    </script>
    ```