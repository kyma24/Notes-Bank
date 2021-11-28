the Math object allows user to perform mathematical tasks, and includes several properties.

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b270f711-772b-4901-971c-6ed8a1f6bd2f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T135639Z&X-Amz-Expires=86400&X-Amz-Signature=bf279b71cfa9d95971244bbb495295c6a03d958dc2a4b110019369a440d58683&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

```jsx
//i.e.
document.write(Math.PI);
```

note that Math has no constructor. There's no need to create a Math object first.

the Math object contains a number of methods that are used for calculations.

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2e064190-0e5e-4f90-93ad-3299b7e35fe0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T135652Z&X-Amz-Expires=86400&X-Amz-Signature=e5bc084433fa420ca293139aad92876a18c778475b1a6161eb481dd2ff2515d9&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

```jsx
//i.e. calculate the sqrt of a number
var number = Math.sqrt(4);
document.write(number);
```

to get random number between 1-10, use Math.random(), which gives a number between 0-1. Then multiply the number by 10, and then take Math.ceil() from it:

Math.ceil(Math.random()\*10).

example: create a program that will as the user to input a number and alert its square root.

```jsx
var n = prompt("Enter a number", "");
var answer = Math.sqrt(n);
alert("The square root of " + n + " is " + answer);
```

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ef3f9710-eda0-4d08-9bcf-c1f338f0585c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T135709Z&X-Amz-Expires=86400&X-Amz-Signature=b8f164c67b958146a1001edb61443c9a7b317324bc41ddc236d0750e6784e908&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

when enter 64:

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b8090eca-827a-4e89-a76f-7bd065d11dca/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T135720Z&X-Amz-Expires=86400&X-Amz-Signature=d64c78db4c4c52f055b4671f7a281d7fbb1da0332c69a804a13ff5e445888638&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)