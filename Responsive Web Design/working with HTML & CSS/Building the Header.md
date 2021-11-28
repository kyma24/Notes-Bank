Now that we have the basic structure of the page, we can start building each of its sections.

Let's start with the header:
![contentImage](https://api.sololearn.com/DownloadFile?id=4577)

We use **h1** and **h2** tags for the texts and an **a** tag for the button. Also, we wrap the whole header on a container div, so we can style it with CSS:
```html
<div class="container">
	<h1>Awesome App</h1>
	<h2>This app will change your life!</h2>
	<a class="btn">Download Now</a>
</div>
```

We define corresponding classes for the container div and the **Download Now** link.

Now it's time to add some CSS styles to the header elements.
Let's start with the **h1** and **h2** tags:
```css
h1 {
	font-size: 48px;
	margin: 0 0 16px 0;
}
h2 {
	font-weight: 300;
	font-size: 24px;
	margin: 0 0 16px 0;
}
```

Here we define the font sizes and margins.

recall how the **margin** values work: the first value is the top margin, the second value is the right margin, third is the bottom margin and the last one defines the left margin. This means the values go in the clockwise direction, starting from the top.

For the **container** div, we will define the following styles:
```css
.container {
	margin: 0 auto;
	padding: 0 20px 0 20px;
	max-width: 900px;
}
```

Since the header takes the full width of the browser, we limited the maximum width the text container can have to 900px using the **max-width** property. This makes the div stop expanding so that the text doesn't get too wide. Because we will reuse the **container** calss for other sections, we defined some left and right **paddings**, which ensures that the child elements stay 20px away from the edges of the screen.

note that **margin: 0 auto;** ensures that the content stays at the center of the container, irrespective of its size. On a screen that is larger than 900 px in width, the **container** div will have the width of 900px, so we align it to the center of the screen.