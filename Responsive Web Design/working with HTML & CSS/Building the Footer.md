The last section of the landing page is the footer:
![contentImage](https://api.sololearn.com/DownloadFile?id=4580)

It contains a menu and copyright text.

It is a common practice to use a list for the menu items:
```html
<footer>
	<div class="container">
		<ul>
			<li><a href="#">Home</a></li>
			<li><a href="#">About</a></li>
			<li><a href="#">Contacts</a></li>
		</ul>
		<p>© All rights reserved.</p>
	</div>
</footer>
```

We have reused the container div to provide the necessary paddings and center alignment.
Each of the menu links are contained in list items.
The copyright text is a simple paragraph.

note that by default, the list items are styled as a vertical bullet list.

Here is the CSS:
```css
footer {
	background: #353535;
	padding: 32px 0;
	text-align: center;
	color: #868686;
	font-size: 12px;
}
footer ul {
	margin: 0;
	padding: 0;
	list-style: none;
}
footer li {
	display: inline-block;
}
footer li a{
	padding: 6px;
	font-size: 14px;
	text-decoration: none;
	color: #c3c3c3;
}
footer li a:hover {
	color: white;
}
```

To make the menu list horizontal and remove the bullets, we used **list-style: none;** for the **ul** element.
We also set **display: inline-block;** for the list items to make them inline-level element containers and so they are positioned next to each other horizontally.

The rest of the styles are simple text and background colors, as well as text sizes.