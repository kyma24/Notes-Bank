-   can be used to replace multiple if-else statements

```jsx
switch (expression) {
	case n1:
		statements
		break;
	case n2:
		statements
		break;
	default:
		statements
}
//If don't understand, just go look at Java's switch statements.
```

```jsx
var day = 2;
switch (day) {
	case 0:
		document.write("Sunday");
		break;
	case 1:
		document.write("Monday");
		break;
	case 2:
		document.write("Tuesday");
		break;
	case 3:
		document.write("Wednesday");
		break;
	case 4:
		document.write("Thursday");
		break;
	case 5:
		document.write("Friday");
		break;
	case 6:
		document.write("Saturday");
		break;
	default:
		document.write("Error");
}

var Day = 3;
switch(Day)
{
	case 6:
		document.write("Saturday");
		break;
	case 7:
		document.write("Sunday");
		break;
	default:
		document.write("Weekday");
}
```

```jsx
var color ="yellow";
switch(color) {
	case "blue":
		document.write("This is blue.");
		break;
	case "red":
		document.write("This is red.");
		break;
	case "green":
		document.write("This is green.");
		break;
	case "orange":
		document.write("This is orange.");
		break;
	default:
		document.write("Color not found.");
}
//note: default block is not needed if there is no need to handle the case when no match is found.
```