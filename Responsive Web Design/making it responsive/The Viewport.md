Before we start making the landing page responsive, we need to cover a few concepts.
The first concept is the **viewport**: the visible area of the webpage.
Usually, a webpage with a fixed width becomes too large to fit the viewport on a small screen, such as a mobile device or tablet. To fix this, browsers on those devices scaled down the entire webpage to fit the screen.

You can control the viewport in HTML5 using a **meta** tag:
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

**width=device-width** sets the width of the page to follow the screen width of the device.
**initial-scale=1.0** sets the initial zoom level when the page is first loaded by the browser.

note that you can also use custom values for the viewport tag; however, in most cases, it is recommended you use the defaults by applying the **device-width** value.