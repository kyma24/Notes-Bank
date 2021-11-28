Let's start by building the features section:
![contentImage](https://api.sololearn.com/DownloadFile?id=4578)

This section contains three features along with an image and text. The features are aligned horizontally next to each other.

We will reuse the **container** div to wrap all the elements of the features section:
```html
<section class="features">
	<div class="container">
	
		<div class="feature">
			<img src="img_blue_pin.png" alt="" />
			<p>An awesome feature</p>
		</div>
		
		<div class="feature">
			<img src="img_blue_chart.png" alt="" />
			<p>An awesome feature</p>
		</div>
		
		<div class="feature">
			<img src="img_blue_msg.png" alt="" />
			<p>An awesome feature</p>
		</div>
	</div>
</section>
```

Each feature is wrapped in a div with class "**feature**", which will be used to position the features.

It contains an image and a paragraph of text. Right now, they are simply positioned below each other, so we need to add some CSS styles to fix that.

In order to position the feature divs next to each other horizontally, we will use **display: inline-block** to make them inline-level block containers and provide a width:
```css
.feature {
	width: 32%;
	display: inline-block;
	font-size: 16px;
}
.feature img {
	width: 40%;
}
```

Because we have 3 features, we gave each feature div 32% of the width of their container.
The remaining space will be left for the space between the elements. We also set the width of the images to 40% of their containers.