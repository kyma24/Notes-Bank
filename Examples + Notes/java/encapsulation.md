4 core concepts in OOP:

-   encapsulation
-   inheritance
-   polymorphism
-   abstraction

Encapsulation is to ensure that the implementation details are not visible to users. The variables of one class will be hidden from the other classes, accessible only through the methods of the current class. This is called **data hiding**

To achieve encapsulation in Java, declare the class' variables as **private** and provide public **setter** and **getter** methods to modify and view the variables' values.

```java
//i.e.
class BankAccount {
	private double balance=0;
	public void deposit(double x) {
		if (x > 0) {
			balance += x;
		}
	}
}
```

this implementation hides the **balance** variable, enabling access to it only through the **deposit** method, which validates the amount to be deposited before modifying the variable.

note: In summary, **encapsulation** provides the following benefits:

-   control of the way data is accessed or modified
-   more flexible and easily changed code
-   ability to change one part of the code without affecting other parts