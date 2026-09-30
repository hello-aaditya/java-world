# Instance methods (overriding) — example & explanation
#### Parent.java
```java
package methodHiding;

public class Parent {
    void display1() {
        System.out.println("Inside Parent-display1 method");
    }
    void display2() {
        System.out.println("Inside parent-display2 Method");
    }
}
```
#### Child.java
```java
package methodHiding;

public class Child extends Parent {
    @Override
    void display2() {
        System.out.println("Inside Child-display2 Method");
    }
}
```
#### Main.java
```java
package methodHiding;

public class Main {

    public static void main(String[] args) {

        Parent p = new Parent();
        p.display1();   // Parent version
        p.display2();   // Parent version

		System.out.println("__________________________________");

        Child c = new Child();
        c.display1();   // inherited Parent.display1()
        c.display2();   // Child overridden version

        System.out.println("__________________________________");

        Parent pr = new Child(); // upcasting
        pr.display1();  // inherited Parent.display1()
        pr.display2();  // Child overridden version (runtime dispatch)
    }
}
```
#### Output
```java
Inside Parent-display1 method
Inside parent-display2 Method
__________________________________
Inside Parent-display1 method
Inside Child-display2 Method
__________________________________
Inside Parent-display1 method
Inside Child-display2 Method
```
#### Explanation
When the method is **non-static**, the focus is always on **which object is created**.  
Because non-static methods depend on the **object**, not the reference.

So if the object is of Child class, then Child’s overridden method will run — even if the reference is of Parent type.
That’s why:
```java
Parent pr = new Child();
pr.display2();
```
will always execute **Child’s display2()**, because at runtime the object is **Child**.
So in simple words:
> “For non-static methods, Java checks the object at runtime.  
The object decides which method will run.”

This is called **overriding**.
# Static methods — method hiding example & explanation
> Replace the instance methods with `static` to demonstrate method hiding.

#### Parent.java
```java
package methodHiding;

public class Parent {
    static void display1() {
        System.out.println("Inside Parent-display1 method");
    }
    static void display2() {
        System.out.println("Inside parent-display2 Method");
    }
}
```
#### Child.java
```java
package methodHiding;

public class Child extends Parent {
    // This hides Parent.display2(), not overrides it
    static void display2() {
        System.out.println("Inside Child-display2 Method");
    }
}
```
#### Main.java
```java
package methodHiding;

public class Main {

    public static void main(String[] args) {

        Parent p = new Parent();
        p.display1();
        p.display2();

        System.out.println("__________________________________");

        Child c = new Child();
        c.display1();
        c.display2();

        System.out.println("__________________________________");

        Parent pr = new Child(); // reference type Parent, object Child
        pr.display1();
        pr.display2(); // calls Parent.display2() because static binding uses reference type
    }
}
```
#### Output
```java
Inside Parent-display1 method
Inside parent-display2 Method
__________________________________
Inside Parent-display1 method
Inside Child-display2 Method
__________________________________
Inside Parent-display1 method
Inside parent-display2 Method
```
#### Explanation
Now when the methods are **static**, everything changes.

Static methods do **not** depend on the object.  
They depend completely on the **reference type**, because static methods are handled at **compile time**.

So if the reference is Parent type, then only Parent’s static method will run — even if the object is Child.

That’s why:
```java
Parent pr = new Child();
pr.display2();   // Parent's static method, not Child's
```
Here Java does **not** care which object is created (`new Child()`),  
it only cares that the reference is of type **Parent**, so Parent’s static method runs.
So in simple words:
> “For static methods, Java checks the reference type at compile time.  
The reference decides which method will run.”

# Method Hiding
Method Hiding happens when both Parent and Child have a **static method with the same signature**.
In this case, the method that gets called depends on **which reference type we are using**, and **does not depends on which object is being created**.

Nothing is actually “overwritten.”  
Nothing is “replaced.”  
Both methods exist separately.

So the real meaning is:

> **“When a static method in the Child has the same signature as the static method in the Parent, Java does not use the Child’s version to replace the Parent version.  
> Instead, whichever reference type you use — Parent or Child — that class’s static method will run.”**

