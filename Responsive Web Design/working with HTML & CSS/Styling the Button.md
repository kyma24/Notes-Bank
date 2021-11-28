The header is almost ready; however, currently the **Download Now** button is just a link w/o any style. To make it look like a button, we need to add the following styles:
```css
.btn {
	display: inline-block;
	color: white;
	font-weight: 500;
	font-size: 20px;
	background: #549DA0;
	border: none;
	border-radius: 5px;
	padding: 12px 16px;
	cursor: pointer;
}
```

The **display** property specifies the display behavior of the element. We have set it to **inline-block** so that the link behaves as an inline block container.

The button also needs to have a hover effect, so it changes its background color when the mouse hovers over it.

To define the style, we will use the **:hover** selector:
```css
.btn:hover {
	background: #468486
}
```

Now, when the cursor hovers over the button, the button's background color changes.