Mediq queries provide the ability to specify different CSS styles for different widths of the viewport, or other specifications.
This makes it possible for a web page to define different layout styles for different screen sizes and make the page responsive!

You define a media query using the **@media** rule inside of the existing style sheet:
```css
@media screen and (max-width: 600px) {
	body {
		background-color: blue;
	}
}
```

The **@media** rule is followed by the media type we are targeting(the screen in our case) and sets the condition when the rules apply(**max_width:600px** in our case).

So now, the style will apply if the page has a width up to 600px.

You can also define multiple conditions, for example a **max** and **min** width of the viewport:
```css
@media screen and (min-width: 800px) and (max-width: 1024px) {
	body {
		background-color: blue;
	}
}
```

Now the style will apply for screen sizes from 800 to 1024 px.

You can also define multiple media queries for a single web page.