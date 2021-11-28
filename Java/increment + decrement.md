```java
class Main 
 {
  public static void main(String[] args) 
  {
    
    int test = 5;
    int a = test++;
    System.out.println(test + "," + a); // (6,5)

// increment x++ > prints & increases value

    int Test = 5;
    int b = ++Test;
    System.out.println(Test + "," + b); // (6,6)

// increment ++x > increases value & prints

    int guess = 5;
    int x = guess--;
    System.out.println(guess + "," + x); // (4,5)

// decrement x-- > prints & decreases value

    int Guess = 5;
    int y = --Guess;
    System.out.println(Guess + "," + y); // (4,4)

// decrement --x > decreases value & prints

  }
}
```