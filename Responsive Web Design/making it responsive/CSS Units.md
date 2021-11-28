An important part of the layout was not using any fixed units for the widths.
We used **percentage** values, which made the elements span relative to the width of their parents.
This approach allows elements to be more flexible, which is essential when putting together a responsive design.

CSS also allows you to define relative unit sizes for **font-sizes:**
The **em** unit size will be relative to the parent's font size.
For example, if the page's body has a font size of **16px**, using **1.5em** will be equal to **24px**(16 x 1.5):
```css
body {
	font-size: 16px;
}
p {
	font-size: 1.5em;
}
```

This is useful bc when you have to change the font size, you need to change it only on the top parent. All child elements will get the corresponding relative size from it using the **em** units.

However, when you define all sizes using **em**, you would be hit by a cascading effect. In this situation, you have many nested elements which use font-sizes relative to their corresponding parents, which results in hard-to-control unit sizes.

Another relative unit is **rem**. It stands for **Root Em**, meaning that it only looks at the font-size of the root element, which is the **html** element. This makes it easier to use than **em**.

Let's change the font-sizes of the landing page to **rem** units:
```css
html {
	font-size: 16px;
}
h1 {
	font-size: 3rem;
	...
}
h2 {
	font-size: 1.5rem;
}
.btn {
	font-size: 1.25rem;
}
```

We set the **html** elements font-size to 16px and uesd that to set all the other font-sizes using **rem**.

This can also be used for margins and paddings.