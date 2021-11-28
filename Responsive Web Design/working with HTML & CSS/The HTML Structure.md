![contentImage](https://api.sololearn.com/DownloadFile?id=4575)
### HTML Structure
Let's start by building the basic HTML structure of our landing page. We will start by building the desktop version and then will adapt it for mobile and make it responsive.
We will use HTML5 semantic tages to define the sections:
```html
<!DOCTYPE html>
<html>
	<head>
		<title>My Landing Page</title>
	</head>
	<body>
		<header>
			header
		</header>
		
		<section class="features">
			features
		</section>
		
		<section class="quote">
			quote
		</section
		
		<footer>
			footer
		</footer>
	</body>
</html>
```

We used a **header** tag for the header, **section** tags for the features and quote sections, and a **footer** tag for the footer.
We gave corresponding class names to the features and quote sections so we can define CSS styles for them.

Now, we need to add some basic CSS styles to give the sections some color and size.
```css
header {
	color: #FFFFFF;
	background-color: #284b63;
	padding: 80px 0;
	text-align: center;
}
section {
	padding: 40px 0;
	text-align: center;
}
.features {
	background: #FFFFFF;
	color: #000000;
}
.quote {
	background: #549DA0;
	color: #FFFFFF
}
footer {
	background: #353535;
	padding: 32px 0;
	text-align: center;
	color: #868686;
}
```

We have used **padding** to give the sections some height.

note that since we provided only two values for the padding, it will set both the **top** and **bottom** padding to the provided value. (**padding: 40px 0;** is the same as **padding: 40px 0 40px 0;**)

we have also defined background and text colors for the sections.

We have not given any width to the sections, so they will occupy the entire width available.

This means that when the screen is resized, the section's width will always remain 100% of the available width.

Since we are planning to create a responsive page, we don't establish any fixed width values for the sections; rather, we make it occupy the entire width of the screen.