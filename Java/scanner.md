```java
import java.util.Scanner;

class MyClass {
    public static void main(String[ ] args) {
        /*
        System.out.println("Please enter a statement.");
        Scanner myVar = new Scanner(System.in);
        System.out.println(myVar.nextLine()); 
        */

        String input = "1 fish 2 fish red fish blue fish";
        Scanner s = new Scanner(input).useDelimiter("\\s*fish\\s*");
        System.out.println(s.nextInt());
        System.out.println(s.nextInt());
        System.out.println(s.next());
        System.out.println(s.next());
        s.close();     
    }
}
```