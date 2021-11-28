Time to make the features section responsive.
It currently includes 3 features aligned next to each other.

On a small screen we want to place them horizontally, with each feature taking the entire width of the container.
Here is the style that we will use in the media query:
```css
.feature {
	width: 100%;
	display: flex;
	align-items: center;
	justify-content: center;
	text-align: left;
	margin: 0 0 10px 0;
	font-size: 16px;
}
.feature img {
	width: 15%;
	min-width: 60px;
	margin-right: 20px;
}
```

We changed the width of each feature div to 100% and set the **display** property to **flex**, which makes the div a **flexbox** container. This allows us to position the child features horizontally and also set the alignment of its child elements -- the icon and the text -- using the **align-items** and **justify-content** properties.
We also set the width of the icons and defined some margins.

Now, the features will be aligned next to each other on larger screens and under each other on smaller screens.

The flexbox layout model allows to create flexible layouts easily, without the need to use CSS positioning and floats.

Let's demonstrate how it works using a simple example:
```html
<div class="container">
  <div>A</div>
  <div>B</div>
  <div>C</div>
</div>
```

To use flexbox, we first define a container and set its **display** property to **flex**.
```css
.container {
	display: flex;
}
```

Now we can play around with the alignments of the child div elements using flexbox properties:
```css
.container {
	display: flex;
	align-items: stretch;
}
.container div {
	flex: 1;
}
```

This will make all child elements have the same width(flex: 1) and fill the entire container width:

([complete flexbox guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/))