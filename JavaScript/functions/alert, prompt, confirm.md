JS offers 3 types of popup boxes: alert, prompt, & confirm.

### Alert Box

alert box is used when you want to ensure that info gets thru to the user.

when an alert box pops up, user must click OK to proceed.

alert function takes a single parameter, which is text displayed in popup box.

```jsx
alert("Do you really want to leave this page?");
```

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/15af95e9-5629-4a1b-80ff-2fe8dc88ef48/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T134645Z&X-Amz-Expires=86400&X-Amz-Signature=e5ebbbf511301b099af4617b82121b0c217fa79c38e2a8eb78a2561e051f7740&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

to display line breaks within popup box, use \\n (like in Python & Java)

```jsx
alert("Hello\\nHow are you?");
```

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3ce6be83-6288-44b2-ab34-0db48e087eff/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T134709Z&X-Amz-Expires=86400&X-Amz-Signature=90273f5b8df83238c41be33ae0fbe5c7cd6cba82db4a1424e3900b33448ebbb1&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

note: be careful when using alert boxes. User can continue using page only after clicking ok.

### Prompt Box

prompt box is often used to have user input value before entering page.

When prompt box pops up, user will have to click either ok/cancel to proceed after entering the input value.

If user clicks OK, the box returns input value. If user clicks cancel, box returns null.

**prompt()** method takes 2 parameters.

-   first is the label, which you want to display in text box
-   second is default string to display in text box(optional)

```jsx
var user = prompt("Please enter your name");
alert(user)
```

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2e9c9346-34eb-4d40-98ea-149988fd9594/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T134728Z&X-Amz-Expires=86400&X-Amz-Signature=46e8d43217b4ad30dbac46a4ae1cbb772aba45120ac1d12dc1ab242a45f126b0&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

note: when prompt box pops up, user will have to click either OK or cancel to proceed after entering input value. Don't overuse method, since it prevents user from accessing other parts of page until box is closed.

### Confirm Box

confirm box is often used to have the user verify/accept something.

when confirm box pops up, user must click either OK or cancel to proceed.

If user clicks OK, box returns true. If user clicks cancel, box returns false.

```jsx
var result = confirm("Do you really want to leave this page?");
if (result == true) {
	alert("Thanks for visiting");
}
else {
	alert("Thanks for staying with us");
}
```

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/53e494ef-dd28-40dd-b64c-252b88fd4ca9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T134752Z&X-Amz-Expires=86400&X-Amz-Signature=da64d58ad9ea2a1a1601cad33ee1b7157b555b90927c8473d02e96e0a0a799f5&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

result when user clicks OK:

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c263ede1-8ac8-4461-ae97-4d72825fdcef/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T134806Z&X-Amz-Expires=86400&X-Amz-Signature=aca10044258e17c64071136d39862a75f8110d5a248c37336681a209ec619119&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

result when user clicks Cancel:

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bae45c8c-44db-4b42-961f-01fe38647dfa/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T134821Z&X-Amz-Expires=86400&X-Amz-Signature=9a29224ab08c1d6a6fc905473d38601d624ef4a8957b24b3f527346dd3c19e03&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

note: also don't overuse, since prevents user from accessing other parts of page until box is closed.