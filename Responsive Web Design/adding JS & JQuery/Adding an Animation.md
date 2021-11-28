Let's use JS to open/close the submenu when the button is tapped.
Since we want to open the submenu using a nice sliding animation, we will use the **JQuery** library, which supports single animations.

We start by including **jQuery** in the page:
```html
<head>
	<title>App Landing Page</title>
	<meta name="viewport" content="width=device-width, intial-scale=1.0">
	<script src="https://code.jquery.com/jquery-3.6.0.js"></script>
</head>
```

We used the **script** tag to import the jQuery library.


Next, we need to handle the click event of the button, which should open and close the submenu.

We will use the **slideToggle()** method, which switches between visible and invisible states of the element selected using a slide animation:
```js
$(function() {
	$(".btn").click(function() {
		$(".submenu").slideToggle(500);
	});
});
```

In the code above, we handled the **click** event of the **.btn**, selected the **.submenu** element and opened/closed it using the **slideToggle** method, providing 500ms for the animation speed.

Now, the only thing left is to hide the submenu by default:
```css
.submenu {
	display: none;
	...
}
```

We have a fully functional submenu, which uses a slide animation.