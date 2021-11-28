```java
class Main {
  public static void main(String[] args) {
    int x = 1;

    while(x > 0)
    {
      System.out.println(x);
      if(x == 4)
        break;
      x++;
    }
    //^^This loops stops after x reaches 4

    for(int x = 10; x <= 40; x = x + 10)
    {
      if(x == 30)
        continue;
      
      System.out.println(x);
    }
    //^^This loop skips the value 30
  }
}
```