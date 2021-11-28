used to avoid name conflicts and to control access to classes.

can be defined as a group made up of similar types of classes, along with sub-packages.

Creating a package in Java is quite easy. Right-click on the **src** directory and click New → Package. Give the package a name and click **Finish**. Will notice that the new package appears in the project directory. Now can move and create classes inside the package.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/83bb9a51-4aad-4eb1-8fac-95c731331694/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/83bb9a51-4aad-4eb1-8fac-95c731331694/Untitled.png)

When moving/creating a class in the package, the following code will appear at the top of the list of files.

```java
package samples;
```

this indicates the package to which the class belongs.

Now need to import the classes that are inside a package in the main to be able to use them.

Following example shows how to use the Vehicle class of the samples package.

```java
import samples.Vehicle;

class MyClass {
  public static void main(String[ ] args) {
    Vehicle v1 = new Vehicle();
    v1.horn();
  }
```

two major results occur when a class is placed in a package. First, the name of the package becomes a part of the name of the class. Second, the name of the package must match the directory structure where the corresponding class file resides.

note: use a wildcard to import all classes in a package.

For example, **import samples.**\* will import all classes in the samples package.