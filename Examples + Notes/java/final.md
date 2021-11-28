use the final keyword to mark a variable constant, so that it can be assigned only once.

```java
//i.e.
class MyClass {
	public static final double PI = 3.14;
	public static void main(String[] args) {
		System.out.println(PI);
	}
}
```

PI is now a constant, any attempt to assign it a value will cause an error.

usually all caps.

note: methods and classes can also be marked final. This serves to restrict methods so that they can't be overridden & classes so that they can't be subclassed.