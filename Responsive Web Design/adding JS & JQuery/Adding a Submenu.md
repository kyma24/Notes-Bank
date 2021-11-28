Modern websites include interactive elements and animations, which improve the user experiene and aesthetics.

Let's add a submenu to the responsive landing page that will open and close when tapping on the **Download Now** button.

The submenu will be responsive as well -- it will appear over elements on desktop, and will push down the elements when on mobile.

Desktop:
![contentImage](https://api.sololearn.com/DownloadFile?id=4583)

Mobile:
![contentImage](https://api.sololearn.com/DownloadFile?id=4584)

We start by creating the submenu using HTML/CSS. The submenu will be a simple div element with links inside the header's **container** div:
```html
<div class="submenu">
	<a href="#">Link 1</a>
	<a href="#">Link 2</a>
</div>
```

We will style it using the following CSS:
```css
.submenu {
	left: 50%;
	transform: translate(-50%, 0);
	text-align: center;
	position: absolute;
	background-color: #549DA0;
	min-width: 160px;
	border-radius: 5px;
	box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
}
.submenu a {
	color: white;
	padding: 12px 16px;
	text-decoration: none;
	display: block;
}
.submenu a:hover {
	background-color: #468486;
}
```

We used a CSS hack in order to position the submenu in the center of the screen. The combination of **absolute** positioning, using the **left** and **transform** properties, results in the submenu being positioned in the center of the screen and opened **over** the page elements.

We also used a **display: block;** for the links, to make them behave as block-level elements.


Time to use CSS in the media query.
We need to make the submenu wider and push down the page, instead of opening it over the elements.
```css
@media screen and (max-width: 480px) {
	.submenu {
		width: 100%;
		position: relative;
	}
	...
}
```

We only need to change the **width** and the **position** properties of the submenu.

note that currently, the submenu is always open. We will add the open/close animation afterwards.