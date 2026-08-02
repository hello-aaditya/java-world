# Real Problem That Leads to Abstraction
Let’s say we have a parent class that represents a general concept.  
Example: A parent class named `Parent` with methods `display1()` and `display2()`.

#### Parent.java
```java
package abstraction;

public class Parent {
    public void display1() {
        System.out.println("Inside Parent-display1 Method");
    }

    public void display2() {
        System.out.println("Inside Parent-display2 Method");
    }
}
```
Now two children override everything:
#### Child1.java
```java
package abstraction;

public class Child1 extends Parent {

    @Override
    public void display1() {
        System.out.println("Inside Child1-display1 Method");
    }

    @Override
    public void display2() {
        System.out.println("Inside Child1-display2 Method");
    }
}
```
#### Child2.java
```java
package abstraction;

public class Child2 extends Parent {

    @Override
    public void display1() {
        System.out.println("Inside Child2-display1 Method");
    }

    @Override
    public void display2() {
        System.out.println("Inside Child2-display2 Method");
    }
}
```
#### Main.java
```java
package abstraction;

public class Main {

    public static void main(String[] args) {

        Parent p1 = new Child1();
        Parent p2 = new Child2();

        accessMethod(p1);
        accessMethod(p2);
    }

    public static void accessMethod(Parent ref) {
        ref.display1();
        ref.display2();
    }
}
```
#### Output
```markdown
Inside Child1-display1 Method
Inside Child1-display2 Method
Inside Child2-display1 Method
Inside Child2-display2 Method
```
#### The Issue
Even though the code works, notice something important:
- Parent’s implementation is **never used**.
- Every child **fully overrides** all methods.
- Parent **doesn’t know the real logic**, children do.

So parent’s method body becomes **meaningless**.  
Parent only knows _method names_, not the _implementation_.

Therefore, it is better to remove all the methods define inside the Parent class-
## What Happens If We Remove Parent Methods?
Let’s remove `display1()` and `display2()` from the parent class completely:
#### Parent.java
```java
package abstraction;

public class Parent {
    // no methods here
}
```
Now children have their own methods:
#### Child1.java
```java
package abstraction;

public class Child1 extends Parent {
    public void display1() {
	    System.out.println("Inside Child1-display1 Method"); 
	}
    public void display2() {
	    System.out.println("Inside Child1-display2 Method");
	}
}
```
#### Child2.java
```java
package abstraction;

public class Child2 extends Parent {
    public void display1() {
	    System.out.println("Inside Child2-display1 Method"); 
	}
    public void display2() {
	    System.out.println("Inside Child2-display2 Method");
	}
}
```
Now, what happens when we upcast?
#### Main.java
```java
package abstraction;

public class Main {

    public static void main(String[] args) {

        Parent p1 = new Child1();
        Parent p2 = new Child2();

        accessMethod(p1);
        accessMethod(p2);
    }

    public static void accessMethod(Parent ref) {
        ref.display1(); // ❌ Compile-time error (Parent has no such method)
        ref.display2(); // ❌ Compile-time error (Parent has no such method)
    }
}
```
Java does not allow it because parent doesn't define the method.
So solution is-
### Using `instanceof` + Downcasting (Ugly Fix)
```java
package abstraction;

public class Main {

    public static void main(String[] args) {

        Parent p1 = new Child1();
        Parent p2 = new Child2();

        accessMethod(p1);
        accessMethod(p2);
    }

    public static void accessMethod(Parent ref) {

	    if (ref instanceof Child1) {
	        ((Child1) ref).display1();
	        ((Child1) ref).display2();
	    }
	
	    if (ref instanceof Child2) {
	        ((Child2) ref).display1();
	        ((Child2) ref).display2();
	    }
	}
}
```
#### Output
```markdown
Inside Child1-display1 Method
Inside Child1-display2 Method
Inside Child2-display1 Method
Inside Child2-display2 Method
```
Yes, the output is correct.
But the approach is **terrible**.
### ❌ Why `instanceof` + downcasting is a horrible approach
##### 1. Breaks Polymorphism
>With `instanceof`, I am deciding which method to call, not the JVM.  
So I lose runtime polymorphism completely.
##### 2. Violates Open/Closed Principle
> Whenever I create a new child class, I must modify the existing method and add another `instanceof`.  
Old code keeps changing — which is against OCP.
##### 3. Not Scalable
>Two subclasses are manageable.  
Ten subclasses become messy.  
Fifty subclasses become a disaster.

## Real Solution- Use Abstract Methods
Parent should define only the **method names**, not the implementation.  
Children will provide the logic.
#### Parent.java
```java
package abstraction;

public abstract class Parent {
    public abstract void display1();
    public abstract void display2();
}
```
#### Child1.java
```java
package abstraction;

public class Child1 extends Parent {
    @Override
    public void display1() {
	    System.out.println("Inside Child1-display1 Method"); 
	}
    @Override
    public void display2() {
	    System.out.println("Inside Child1-display2 Method");
	}
}
```
#### Child2.java
```java
package abstraction;

public class Child2 extends Parent {
    @Override
    public void display1() { System.out.println("Inside Child2-display1 Method"); }
    @Override
    public void display2() { System.out.println("Inside Child2-display2 Method"); }
}
```
#### Main.java
```java
package abstraction;

public class Main {
    public static void main(String[] args) {
        Parent p1 = new Child1();
        Parent p2 = new Child2();
        accessMethod(p1);
        accessMethod(p2);
    }

    public static void accessMethod(Parent ref) {
        ref.display1();
        ref.display2();
    }
}
```
#### Output
```markdown
Inside Child1-display1 Method
Inside Child1-display2 Method
Inside Child2-display1 Method
Inside Child2-display2 Method
```
# Abstraction
Abstraction means **showing only the essential details** and **hiding the implementation**.

In OOP terms:
> 	Parent Class tells _what_ must be done.  
> 	Children Class tell _how_ it will be done.

This is achieved using **abstract classes** and **abstract methods**.

A parent class defines abstract methods (only method names, no body),  
and child classes provide their own implementation (how to do). 

This allows **polymorphism** + **inheritance** + **upcasting** without using `instanceof`.