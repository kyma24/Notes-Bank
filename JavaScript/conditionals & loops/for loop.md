```jsx
//classic loop
for (statement 1; statement 2; statement 3) {
	code block to be executed
}
```

-   statement 1 is executed before the loop starts
-   statement 2 defines condition for running the loop
-   statement 3 is executed each time after loop

in other words, SAME THING AS JAVA

```jsx
for (i = 1; i <= 5; i++) {
	document.write(i + "<br />");
```

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4d291d52-21ed-48f6-9aa3-ad2833af24fc/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T134044Z&X-Amz-Expires=86400&X-Amz-Signature=36c61465aa6644a5a42061afa18531ae949b3e511a951be063013e7a8c66accc&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

statement 1 is optional if value(s) is set before loop starts

```jsx
var i = 1;
for (; i <= 5; i++) {
	document.write(i + "<br />");
}
```

can also initiate more than one value in statement 1 using commas to separate them

```jsx
for (i = 1, text=""; i <= 5; i++) {
	text = i;
	document.write(i + "<br />");
}
```

if put break inside loop, statement 2 is optional.

in addition, statement 3 is optional, but only if you increment values inside loop.

```jsx
var i = 0;
for (; i < 10; ) {
	document.write(i);
	i++;
}
```