Now that we know how to define CSS styles for different screen sizes, we can start making the landing page responsive.

A typical breakpoint for a mobile screen is **480px** width.
Let's define the viewpoint and empy media query target for the landing page:
```css
@media screen and (max-width: 480px) {

}
```

We will create separate styles for our sections when the screen size is lower than 480px in width(this is the typical breakpoint for mobile devices).

On a mobile screen we want to change the text-size of the header texts and make the **Download Now** button span the entire width of the container.

To accomplish this, we define the corresponding styles in the media query:
```css
@media screen and (max-width: 480px) {
	.btn {
		display: block;
		font-size: 18px;
	}
	h1 {
		font-size: 32px;
		margin: 0 0 8px 0;
	}
	h2 {
		font-size: 18px;
	}
	section {
		padding: 25px 0 15px 0;
	}
}
```

As you can see, we changed some of the **font-size** properties, changed the **paddings** of the section container, and changed the button's **display** property to **block**, making it a block level element which takes the whole width of its container.

The result on a mobile screen:
![contentImage](https://api.sololearn.com/DownloadFile?id=4581)

The same header on a larger screen:
![contentImage](https://api.sololearn.com/DownloadFile?id=4577)