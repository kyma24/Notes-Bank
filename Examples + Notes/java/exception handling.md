an exception is a problem that occurs during program execution. Exceptions cause abnormal termination of the program.

Exception handling is a powerful mechanism that handles runtime errors to maintain normal application flow.

An exception can occur for many different reasons. Some examples:

-   a user has entered invalid data
-   a file that needs to be opened can't be found
-   a network connection has been lost in the middle of communications
-   insufficient memory and other issues related to physical resources

as seen, exceptions are caused by user error, programmer error, or physical resource issues. However, a well-written program should handle all possible exceptions.

exceptions can be caught using a combination of the **try** and **catch** keywords.

A try/catch block is placed around the code that might generate an exception

```java
try {
	//some code
} catch(Exception e) {
	//some code to handle errors
}
```

a catch statement involves declaring the type of exception that is intended to be caught. If an exception occurs in the try block, the catch block that follows the try is checked. If the type of exception that occurred is listed in a catch block, the exception is passed to the catch block much as an argument is passed to a method parameter.

The Exception type can be used to catch all possible exceptions.

```java
//i.e. exception handling when trying to access array index that doesn't exist:
public class MyClass {
	public static void main(String[] args) {
		try{
			int a[] = new int[2];
			System.out.println(a[5]);
		} catch(Exception e) {
			System.out.println("An error occurred");
		}
	}
}
```

w/o the try/catch block this code could crash the program, as a\[5\] does not exist.

Notice the (Exception e) statement in the catch block - it is used to catch all possible exceptions.