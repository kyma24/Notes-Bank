```html
<article>
	<h1>The article title</h1>
	<p>Contents of article element</p>
</article>

<!-- article: self-contained/independent piece of content that can be used/distributed seperately from rest of page/site -->
<!-- examples of usage: forum post, a magazine or newspaper article, a blog entry, a comment, an interactive widget or gadget, or any other independent piece of content. -->

<!-- article element replaces <div> in HTML 4 along w/ id or class -->
<!-- nested article elements = a part that is related to the larger part(i.e. comments on blog post) -->
```

```html
<article>
	<h1>Welcome</h1>
	<section>
		<h1>Heading</h1>
		<p>content or image</p>
	</section>
</article>

<!-- section is logical container of page/article. Can be used to divide up content within article: i.e. homepage could have section for introducing company, another for news items, and another for contact info -->
<!--each section typically identified using headig as child of the section element-->

<!-- if it makes sense to separately syndicate the content of a <section> element, use an <article> element instead -->
```

```html
<article>
	<h1>Gifts for everyone</h2>
	<p>This website will be the best place for choosing gifts</p>
	<aside>
		<p>Gifts will be delivered to you within 24 hours</p>
	</aside>
</article>

<!-- aside tag is secondary or tangential content which could be considered separate from but indirectly related to the main content-->
<!-- type of data often represented in sidebars-->
<!--when <aside> tag is used within <article> tag, content of <aside> tag should be related to that article -->
<!--when <aside> tag is used outside <article> tag, content should be related to surrounding content(secondary content)-->
```