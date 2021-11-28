-   DOM: Document Object Model
    
    ```html
    <!DOCTYPE html>
    <html>
    	<head>
    		<meta charset = "utf-8">
    		<title>The DOM (Document Object Model)</title>
    	</head>
    	<body>
    		<h1> DOM: Document Object Model</h1>
    		<p>Manipulating the DOM:</p>
    		<ol>
    			<li>Find the DOM node using an access method.
    			<!--If want body, then do document.body: can find elements w/ same id, or different types of tags-->
    			<li>Manipulate the DOM node by changing its attributes, styles, inner HTML, or appending new nodes to it.
    			<!--i.e. innerHTML to replae everything on the page-->
    		</ol>
    
    		<script>
    		document.body.innerHTML("HEllo there OVERRIDE");
    		</script>
    ```
    
    -   DOM access methods
        
        -   `[document.getElementById(id)](<https://developer.mozilla.org/en-US/docs/Web/API/document.getElementById>)`
            
        -   `[document.getElementsByClassName(className)](<https://developer.mozilla.org/en-US/docs/Web/API/document.getElementsByClassName>)`
            
        -   `[document.getElementsByTagName(tagName)](<https://developer.mozilla.org/en-US/docs/Web/API/document.getElementsByTagName>)`
            
        -   `[document.querySelector(cssSelector)](<https://developer.mozilla.org/en-US/docs/Web/API/document.querySelector>)`
            
        -   `[document.querySelectorAll(cssSelector)](<https://developer.mozilla.org/en-US/docs/Web/API/document.querySelectorAll>)`
            
        -   document.getElementById()
            
            changing website abt dogs into a website abt cats
            
            ```html
            <!DOCTYPE html>
            <html>
                <head>
                    <meta charset="utf-8">
                    <title>Finding elements by ID</title>
                </head>
                <body>
            
                    <h1 id="heading">All about dogs</h1>
                    
                    <p>The domestic <span class="animal">dog</span> is known as man's best friend. The <span class="animal">dog</span> was the first domesticated animal and has been widely kept as a working, hunting, and pet companion. According to recent coarse estimates, there are currently between 700 million and one billion <span class="animal">dog</span>s, making them the most abundant predators in the world. <a href="<http://en.wikipedia.org/wiki/Dog>">Read more on Wikipedia</a>.</p>
                    
                    <img src="<https://www.kasandbox.org/programming-images/animals/dog_sleeping-puppy.png>" height="150" alt="Sleeping puppy">
                    
                    <img src="<https://www.kasandbox.org/programming-images/animals/dogs_collies.png>" height="150" alt="Dogs running">
                    
                    <script>
                    /* 
                    1. Find the DOM node using an access method.
                    2. Manipulate the DOM node by changing its attributes, styles, inner HTML, or appending new nodes to it.
                    */
            				**var headingEl = document.getElementById("heading");**
            				//gets element w/ id
            				//ending variable w/ el or node notifies us that it is abt an element
            				console.log(headingEl);
            				headingEl.innerHTML = "All about cats";
            				//turns heading into "All about cats"
                    </script>
                </body>
            </html>
            ```
            
        -   document.getElementsByTagName();
            
            ```html
            <!DOCTYPE html>
            <html>
                <head>
                    <meta charset="utf-8">
                    <title>Finding elements by ID</title>
                </head>
                <body>
            
                    <h1 id="heading">All about dogs</h1>
                    
                    <p>The domestic <span class="animal">dog</span> is known as man's best friend. The <span class="animal">dog</span> was the first domesticated animal and has been widely kept as a working, hunting, and pet companion. According to recent coarse estimates, there are currently between 700 million and one billion <span class="animal">dog</span>s, making them the most abundant predators in the world. <a href="<http://en.wikipedia.org/wiki/Dog>">Read more on Wikipedia</a>.</p>
                    
                    <img src="<https://www.kasandbox.org/programming-images/animals/dog_sleeping-puppy.png>" height="150" alt="Sleeping puppy">
                    
                    <img src="<https://www.kasandbox.org/programming-images/animals/dogs_collies.png>" height="150" alt="Dogs running">
                    
                    <script>
                    /* 
                    1. Find the DOM node using an access method.
                    2. Manipulate the DOM node by changing its attributes, styles, inner HTML, or appending new nodes to it.
                    */
            				var headingEl = document.getElementById("heading");
            				console.log(headingEl);
            				headingEl.innerHTML = "All about cats";
            				
            				**var nameEls = document.getElementsByTagName("span");**
            				//to check whether code is right, do console.log.
            				console.log(nameEls);
            				//HTMLCollection
            				console.log(nameEls[0]);
            				~~nameEls.innerHTML = "cat";~~
            
            				//changing "dogs" to "cats":
            				for (var i = 0; i < nameEls.length; i++) {
            					nameELs[i].innerHTML = "cat";
            				}
                    </script>
                </body>
            </html>
            ```
            
            -   example: nametag
                
                ```html
                <!DOCTYPE html>
                <html>
                    <head>
                        <meta charset="utf-8">
                        <title>Challenge: Custom name tags</title>
                        <style>
                            * {
                                box-sizing: border-box;
                            }
                            
                            .name-tag {
                                border: 1px solid red;
                                border-radius: 6px;
                                width: 300px;
                                height: 150px;
                                margin-bottom: 10px;
                                background: red;
                                font-family: sans-serif;
                            }
                            
                            .name-tag h1 {
                                color: white;
                                text-align: center;
                                height: 25px;
                                margin: 5px 0px 0px 0px;
                                font-size: 20px;
                            }
                            .name-tag p {
                                position: relative;
                                left: 5px;
                                padding: 10px;
                                width: 290px;
                                height: 90px;
                                background: white;
                                font-family: cursive;
                                font-size: 20px;
                                text-align: center;
                            }
                        </style>
                    </head>
                    <body>
                
                        
                        <div class="name-tag">
                            <h1>Hello, my name is...</h1>
                            <p>Grace Hopper</p>
                        </div>
                        
                        <div class="name-tag">
                            <h1>Hello, my name is...</h1>
                            <p>Alan Turing</p>
                        </div>
                        
                        <script>
                            var nameEls = document.getElementsByTagName("h1");
                            
                            for (var i = 0; i < nameEls.length; i++) {
                                nameEls[i].innerHTML = "Allo";
                            }
                        </script>
                    </body>
                </html>
                ```
                
        -   document.querySelector();
            
            ```html
            <!DOCTYPE html>
            <html>
            	<head>
            		<meta charset="utf-8">
            		<style>
            			p .animal {
            				color: red;
            			}
            		</style>
            	</head>
            	<body>
            		<p>The domestic <span class="animal">dog</span> is known as man's best friend.The <span class="animal">dog</span> was the first domesticated animal and has been widely kept as a working, hunting, and pet companion.</p>
            
            		<script>
            			var nameEls = document.querySelectorAll("p.animal");
            			console.log(nameEls);
            			//HTMLCollection
            			console.log(nameEls[0]);
            			for (var i = 0; i < nameEls.length; i++) {
            				nameEls[i].innerHTML = "cat";
            			}
            			//changes all "dog" into "cat"
            		</script>
            	</body>
            </html>
            ```
            
    -   Accessing w/ sub-queries
        
        once you've found an element, you can do subqueries on it using the method querySelectorAll(), which returns a NodeList, which also acts like an array. The list is static, which means that the list won't update even if new matching elements are added to page. Most likely won't run into the difference between the 2 data return types when using the methods:
        
        ```jsx
        var teamMembers = document.querySelectorAll(".team-member");
        for (var i = 0, i < teamMembers.length; i++) {
        	console.log(teamMembers[i].innerHTML);
        }
        ```
        
        for sub-queries, i.e.
        
        ```jsx
        //find the element w/ that ID
        var motto = document.getElementById("motto");
        //find the spans inside that element
        var mottoWords = motto.getElementsByTagName("span");
        //log out how many there are
        console.log(mottoWords.length);
        ```
        
    -   traversing the DOM
        
        another way to access elements is to "traverse" the DOM tree. Each element has properties that point to elements related to it:
        
        -   firstElementChild,
        -   lastElementChild,
        -   nextElementChild/nextElementSibling,
        -   previousElementChild/previousElementSibling,
        -   childNodes,
        -   & childElementCount.
        
        i.e.
        
        ```jsx
        var motto = document.getElementById("motto");
        for (var i = 0; i < motto.childNodes.length; i++) {
        	console.log(motto.childNodes[i]);
        }
        ```
        
        note: these properties aren't available on Text nodes, only on Element nodes. To make sure you can traverse an element, you can check its nodeType/nodeValue properties. you likely won't need/want to use DOM traversal, but it's a option.