-   React with Next.js
    -   basics
        
        React = web framework
        
        like CSS, can be used with HTML
        
        take React code & compile it into HTML
        
        can add on addons to the code
        
        using JS to simulate HTML is called **React**.
        
        ```jsx
        function HomePage() {
        	return {
        		<div>
        			{//can insert JavaScript into here
        				new Array(len).fill(<div>
        					<a href="<https://google.com>">heedr</a>
        				</div>
        			)}
        		</div>
        	}
        }
        ```
        
        ```jsx
        const Heedr = () => (
        	<div>
        		<a href="<https://google.com>">heedr</a>
        	</div>
        }
        //this syntax does the same as before/below, can use it in the function below.
        
        function HomePage() {
        	return (
        		<div>
        			<Heedr/> //like custom tag!
        		</div>
        	)
        }
        
        export default HomePage
        ```
        
        inline JS = inline CSS for JS
        
        ```jsx
        //in react,
        const Heedr = () => (
        	<div>
        		<a style={{
        			color:"red",
        			fontSize:"30px",
        			textDecoration:"none"
        		}} href="<https://google.com>">heedr</a>
        	</div>
        )
        ```
        
        npm i next react react-dom
        
        npm init
        
        creating a new page on website:
        
        1.  create new file, like HTML(similar structure)
        2.  save another file
        
        ```jsx
        //to get to another page,
        import Link from "next/link"
        ```
        
        this takes the link and puts it in variable Link
        
        ```jsx
        <Link href="/claire">
        	<Heedr/>
        </Link>
        ```
        
        this turns the Heedr output into a link that gets redirected to page claire. Don't need the .html in React.
        
        to use this, turn the a tag in const Heedr into a paragraph tag.
        
        whenever clicking on the Heedr output, the HTML gets turned server side and stuff.
        
    -   index
        
        type in `npm i theme-ui` into the shell to download theme-ui
        
        [](https://github.com/system-ui/theme-ui)[https://github.com/system-ui/theme-ui](https://github.com/system-ui/theme-ui)
        
        call new file `_app.js`. this will be run first, before everything else, like a loading page.(similar to main)
        
        npm i @theme-ui/preset-deep
        
        [Intro to React Workshop](https://www.notion.so/Intro-to-React-Workshop-e186ac8035d74a5fa1834a477372318b)
        
        ```jsx
        import Link from "next/link"
        import {Heading} from "@theme-ui/components"
        
        function HomePage() {
        	return {
        		<div>
        			<Heading sx={{
        				textAlign:"center",
        				marginTop: "20px",
        				marginBottom: "20px",
        				//is equal to
        				my: "20px",
        				//in React
        
        				//making it responsive depending on page size:
        				fontSize:[4,6,7]
        				//inside theme imported, h1-h6 are predefined in this array(if larger, would become what would be thought of as that size)
        				//as the screen size increases, the font grows with it.
        			}}>TARDIS</Heading>
        		</div>
        	}
        }
        
        export default HomePage
        	
        ```