```jsx
function main() {
    var distance = parseInt(readLine(), 10);
    //^is eval(input()) in python(basically)
    var speed = 40;
    var hours = distance/speed;
    var seconds = hours * 60;
    console.log(seconds);
}
//distance/speed/time calculation when going 40 mph(time in seconds)
```