```java
class Main {
  public static void main(String[] args) {
    //nested if statement
    int age = 25;
    if(age > 0)
		{
      if(age > 16)
        System.out.println("Welcome!");
      else
        System.out.println("Too young!");
		}
    else
      System.out.println("Error");

    //else if statement
    int Age = 25;
    if(Age <= 0)
      System.out.println("Error");
    else if(age <= 16)
      System.out.println("Too young");
    else if(age < 100)
      System.out.println("Welcome!");
    else
      System.out.println("Really?");
		//logical statements
    int money = 229;
    if(age > 18)
    {
      if(money > 500)
        System.out.println("Welcome!");
    }

    if(age > 18 && money > 500)
      System.out.println("Welcome!");

		//or operator: ||
    if(age > 18 || money > 500)
      System.out.println("Welcome!");
    
    //not operator: !()
    if(!(age > 18))
      System.out.println("Too young");
    else
      System.out.println("Welcome!");
  }
}
```