an Enum is a special type used to define collections of constants.

```java
//i.e.
enum Rank {
	SOLDIER,
	SERGEANT,
	CAPTAIN
}
```

note that values are comma-separated.

The constants can be referred to with the dot syntax.

```java
Rank a = Rank.SOLDIER;
```

basically, Enum define variables that represent members of a fixed set.

After declaring an Enum, can check for the corresponding values with, for example, a switch statement.

```java
Rank a = Rank.SOLDIER;

switch(a) {
	case SOLDIER:
		System.out.println("Soldier says hi!");
		break;
	case SERGEANT:
		System.out.println("Sergeant says Hello!");
		break;
	case CAPTAIN:
		System.out.println("Captain says Welcome!");
		break;
}
```

Should always use Enums when a variable(especially a method parameter) can only take one out of a small set of possible values.

If Enums are used instead of integers(or String codes), you increase compile-time checking and avoid errors from passing in invalid constants, and you document which values are legal to use.

note: Some sample Enum uses include month names, days of the week, deck of cards, etc.