For the quote section, we will just change the text size and some paddings:
```css
.quote {
	padding: 30px 0;
}
blockquote p {
	font-size: 18px;
}
blockquote cite {
	font-size: 14px;
}
```

We don't need to change the position of the section elements, as they are already aligned to the center of the screen.


Last but not least, we need to change the footer section.

We need to position the menu links below each other:
```css
footer {
	padding: 30px 0 10px 0;
}
footer li {
	display: block;
	margin: 5px 0;
}
```

The **display:block;** style makes the list items block level elements so they take the entire width of their container. This makes the items align under each other:
![contentImage](https://api.sololearn.com/DownloadFile?id=4582)

The same footer on a large screen:
![contentImage](https://api.sololearn.com/DownloadFile?id=4580)

Now the landing page is fully responsive, having different layouts for mobile and desktop screens.