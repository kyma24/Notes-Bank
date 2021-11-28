Java supports **nesting** classes; a class can be a member of another class.

Creating an inner class is quite simple. Just write a class within a class. Unlike a class, an inner class can be private. Once an inner class is declared private, it can't be accessed from an object outside the class.

```java
class Robot {
	int id;
	Robot(int i) {
		id = i;
		Brain b = new Brain();
		b.think();
	}

	private class Brain {
		public void think() {
			System.out.println(id + " is thinking");
		}
	}

}
```

the class Robot has inner class Brain. The inner class can access all of the member variables and methods of its outer class, but it can't be accessed from any outside class.