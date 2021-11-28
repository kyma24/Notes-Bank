the **throw** keyword allows the user to manually generate exceptions from the methods. Some of the numerous available exception types include the IndexOutOfBoundsException, IllegalArgumentException, ArithmeticException, and so on.

i.e., an ArithmeticExpression can be thrown in the method when the parameter is 0.

```java
int div(int a, int b) throws ArithmeticException {
	if(b == 0) {
		throw new ArithmeticExpression("Division by Zero");
	} else {
		return a / b;
	}
}
```

the **throws** statement in the method defines the type of Exception(s) the method can throw.

Next, the throw keyword throws the corresponding exception, along with a custom message.

If the div method is called with the second parameter equal to 0, it will throw an ArithmeticException with the message "Division by Zero".

note: Multiple exceptions can be defined in the throws statement using a comma-separated list.

A single try block can contain multiple catch blocks that handle different exceptions separately.

```java
//i.e.
try {
	//some code
} catch (ExceptionType1 e1) {
	//Catch block
} catch (ExceptionType2 e2) {
	//Catch block
} catch (ExceptionType3 e3) {
	//Catch block
}
```

all catch blocks should be ordered from most specific to most general.

following the specific exceptions, can use the **Exception** type to handle all other exceptions as the last catch.