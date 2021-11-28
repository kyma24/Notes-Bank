anonymous classes are a way to extend the existing classes on the fly.

i.e. consider having a class Machine:

```java
class Machine {
	public void start() {
		System.out.println("Starting...");
	}
}
```

When creating the Machine object, we can change the start method on the fly.

```java
public static void main(String[] args) {
	Machine m = new Machine() {
		@Override public void start() {
			System.out.println("Woooooo");
		}
	};
	m.start();
}
```

after the constructor call, have opened the curly braces and have overridden the start of method's implementation on the fly.

note: the @Override annotation is used to make your code easier to understand, because it makes it more obvious when methods are overridden.

The modification is applicable only to the current object, and not the class itself. So if another object of that class is created, the start method's implementation will be the one defined in the class.

```java
class Machine {
	public void start() {
		System.out.println("Starting...");
	}
}
public static void main(String[] args) {
	Machine m1 = new Machine() {
		@Override public void start() {
			System.out.println("Wooooo");
		}
	};
	Machine m2 = new Machine();
	m2.start();
} 
```