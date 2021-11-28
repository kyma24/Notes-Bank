```jsx
function main() {
    var depth = parseInt(readLine(), 10);
    var days = 0;
    for (i = 0; i < depth; ) {
        days += 1;
        i += 7;
        if (i >= depth) {
            break;
        }
        i -= 2;
    }
    console.log(days);
}
```