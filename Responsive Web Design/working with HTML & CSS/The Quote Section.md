The quote section contains a testimonial from a satisfied customer:
![contentImage](https://api.sololearn.com/DownloadFile?id=4579)

Let's build the HTML using semantic tags:
```html
<section class="quote">
	<blockquote class="container">
		<p>"Some great quote!"</p>
		<cite>Satisfied Customer</cite>
	</blockquote>
</section>
```

We used the **blockquote** tag as the container and reused the **container** class on it.
Inside the blockquote, we have a paragraph of text representing the quote, and a **cite** tag, containing the name of the customer.

note that the **blockquote** element specifies a section that is quoted, while **cite** is used to define a title.

Time to define the styles.
```css
blockquote {
	margin: 0;
	padding: 0;
	text-align: center;
}
blockquote p {
	margin: 0 0 5px 0;
	font-size: 24px;
}
blockquote cite {
	font-size: 16px;
	font-style: italic;
}
blockquote cite:before{
	content: '-';
	margin-right: 5px;
}
```

First, we need to reset the padding/margin of the **blockquote** element since the browsers have some default values for them.
We also need to define the font sizes and margins for the elements.

Last but not least, we use the **:before** selector to set a dash before the **cite** element.

note that we could have added the dash in the text of the **cite** tag, but this is a fancier way of doing the same thing.