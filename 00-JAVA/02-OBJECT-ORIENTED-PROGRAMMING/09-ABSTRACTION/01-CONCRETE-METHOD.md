# Concrete Method
A **concrete method** is a normal method with a complete body.  
Even inside an abstract class, if we provide the full method definition, it is called a **concrete method**.

### Example: Abstract + Concrete Methods Together

#### Parent.java
```java
package abstraction;

public abstract class Parent {

    // incomplete → must be implemented by children
    abstract void display1();
    abstract void display2();

    // complete method → concrete method
    void display3() {
        System.out.println("Inside Parent-display3 Method");
    }
}
```
#### Child1.java
```java
package abstraction;

public class Child1 extends Parent {
    void display1() {
	    System.out.println("Inside Child1-display1 Method");
	}
    void display2() {
	    System.out.println("Inside Child1-display2 Method");
	}
}
```
#### Child2.java
```java
package abstraction;

public class Child2 extends Parent {
    void display1() {
	    System.out.println("Inside Child2-display1 Method");
	}
    void display2() {
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
        ref.display3();   // concrete method from parent
    }
}
```
#### Output
```markdown
Inside Child1-display1 Method
Inside Child1-display2 Method
Inside Parent-display3 Method
Inside Child2-display1 Method
Inside Child2-display2 Method
Inside Parent-display3 Method
```

# Abstract Method vs Concrete Method
|Feature|**Abstract Method**|**Concrete Method**|
|---|---|---|
|**Definition**|Method with **no body**|Method with a **complete body**|
|**Purpose**|Defines **what** must be done|Defines **how** it is done|
|**Implementation**|Must be implemented by child classes|Already implemented in the parent class|
|**Keyword**|Uses `abstract` keyword|No special keyword|
|**Ending**|Ends with `;`|Ends with `{ }` body|
|**Class Requirement**|Can exist **only in an abstract class**|Can exist in **any class** (abstract or normal)|
|**Overriding**|Child classes **must** override|Child classes **may** override (optional)|
|**Polymorphism**|Helps achieve polymorphism (forced overriding)|Provides reusable common behavior|
|**Usage**|When parent cannot define logic|When parent wants to share common logic|
|**Example**|`abstract void show();`|`void show(){ System.out.println("..."); }`|

> **Concrete method = common code once**  
>**Abstract method = force children to implement**