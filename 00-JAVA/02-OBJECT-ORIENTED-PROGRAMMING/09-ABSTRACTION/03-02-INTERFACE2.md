# 1. Marker Interface (or Tagged Interface)
> A **marker interface** is an interface that contains **no methods** and **no variables**.  
It is completely empty.
### 1.1 Why do we use it?
A marker interface is used to **mark** or **tag** a class with a special meaning.  
Java uses these tags internally to provide special behavior during runtime.

#### Example:
##### MyMarker.java
```java
interface MyMarker {
    // no methods → marker interface
}
```
##### Demo.java
```java
class Demo implements MyMarker {
    // class is now “tagged”
}
```
### 1.2 Real Examples in Java**
These are famous built-in marker interfaces in Java:
- **Serializable**  
    → Marks a class eligible for serialization.
# 2. Interface and Multiple Inheritance
Java does **not** support multiple inheritance with classes, meaning:
```java
class A {}
class B {}
class C extends A, B {}   // ❌ Not allowed
```
But Java **does** support multiple inheritance through **interfaces**.
## 2.1 Why is this allowed?
Because interfaces contain only method declarations (no implementation conflicts).

So, one interface can extend multiple interfaces, and a class can implement multiple interfaces safely.
### 2.20 Example: 
#### 2.21 Interface Extending Multiple Interfaces
```java
interface A {
    void m1();
}

interface B {
    void m2();
}

interface C extends A, B {
    void m3();
}
```
✔ `C` inherits `m1()` from A  
✔ `C` inherits `m2()` from B  
✔ No conflict → all methods are abstract
#### 2.22 Class Implementing Multiple Interfaces
```java
interface A { void m1(); }
interface B { void m2(); }

class Test implements A, B {
    public void m1() { System.out.println("m1"); }
    public void m2() { System.out.println("m2"); }
}
```
✔ Class implements both sets of rules  
✔ No ambiguity  
✔ Pure multiple inheritance

#### 2.23 Practical Example
```java
interface Calculator1 {
    void add();
    void sub();
}

interface Calculator2 extends Calculator1 {
    void mul();
    void div();
}

class MyCalculator implements Calculator2 {
    // implements all methods from both Calculator1 and Calculator2
}
```
`Calculator2` already extends `Calculator1`, so implementing `Calculator2` gives all methods together.

# 3. Default Method in Interface (Java 8 Feature)
Before Java 8, interfaces could contain **only abstract methods**.  
But Java 8 introduced **default methods**, which allow interfaces to have **method bodies**.

To add new methods to existing interfaces **without breaking old code**.
So Java said:

> **Let the interface provide a default implementation.  
> Old classes don’t need to override it unless they want to.**

## 3.1 Syntax of Default Method
```java
interface A {
    default void display() {
        System.out.println("Default display");
    }
}
```
- Uses the keyword **default** (not the access specifier `default`).
- Has a **method body**.
- Optional for child class to override.
#### 3.2 Example:
##### Shape.java
```java
interface Shape {
    void draw();

    default void info() {
        System.out.println("This is a shape");
    }
}
```
#### Square.java
```java
class Square implements Shape {
    public void draw() {
        System.out.println("Drawing Square");
    }
}
```
##### Main.java
```java
class Main {
    public static void main(String[] args) {
        Shape s = new Square();
        s.draw();
        s.info();   // calling default method
    }
}
```
##### Output
```markdown
Drawing Square
This is a shape
```
✔ `Square` inherited the default method  
✔ `Square` didn't need to override it  
✔ If needed, `Square` **can** override `info()`

---
#### Note:
Inside a **class**, we cannot use `default` keyword for methods.
```java
class A {
    default void show() {}   // ❌ Not allowed in class
}
```
Default keyword works **only** inside interfaces.

---
# 4. static Method in Interface (Java 8 Feature)
Just like default methods, Java 8 also introduced **static methods inside interfaces**.
Now, an interface can have static methods with a complete body.
## 4.1 Why static methods were added?
To allow interfaces to provide **utility/helper methods** that belong to the interface itself —  
not to the objects that implement it.

Java already had static utility classes like `Collections`, `Arrays`, etc.  
This feature allows the same behavior inside interfaces.
### 4.2 Syntax of static method inside interface
```java
interface A {
    static void show() {
        System.out.println("Static method inside interface");
    }
}
```
✔ Has a method body  
✔ Must use keyword **static**  
✔ Cannot be overridden by implementing classes
#### 4.3 How to call static method inside an interface?
Static methods are **called using the interface name**, not the object
```java
A.show();  
```
we **cannot** call it through an object or through upcasting, like-
```java
A obj = new B();
obj.show();   // ERROR – static methods do not belong to the object
```
It is wrong.
### 4.4 Example
##### Calculator.java
```java
interface Calculator {
    static void info() {
        System.out.println("This is Calculator Interface");
    }
}
```
##### Main.java
```java
class Main {
    public static void main(String[] args) {
        Calculator.info();  // calling static method
    }
}
```
##### Output
```markdown
This is Calculator Interface
```
### 4.5 Important Rules
1. **Static methods inside interface must have a body.**
2. **Cannot override static methods in implementing classes.**
3. **Static methods are not inherited by the child class.**
4. **Must be called using InterfaceName.methodName().**
---
# 5. private Method in Interface (Java 9 Feature)
From Java 9 onward, interfaces can have **private methods**.

## 5.1 Why private methods were introduced?
> Private methods in interfaces are only for internal use inside the interface.

Implementing classes cannot see or override them.
## 5.2 Types of private methods allowed
1. **private instance method**
2. **private static method**

Both must **have a body**.
## 5.3 Syntax
#### private instance method:
```java
interface A {
    private void helper() {
        System.out.println("Helper logic");
    }
}
```
#### private static method:
```java
interface A {
    private static void util() {
        System.out.println("Static helper logic");
    }
}
```
✔ These methods are **not** accessible outside the interface.  
✔ Can be used only by **default methods** and **static methods** inside the same interface.
#### 5.4 Example
##### Shape.java
```java
interface Shape {

    default void info() {
        log("Displaying info...");
    }

    static void details() {
        log("Showing details...");
    }

    private static void log(String msg) {
        System.out.println(msg);
    }
}
```
##### Output
```markdown
Shape.info();     // through object of implementing class
Shape.details();  // directly through interface
```
Internally:
- `info()` calls private static `log()`
- `details()` also calls the same private static `log()`

But implementing classes never see `log()` — it stays hidden.
## 5.5 Important Rules

1. **Private methods must have a body.**
2. **Private methods cannot be abstract.**
3. **Private methods are not inherited.**
4. **Private methods cannot be overridden.**
5. **Used only by default and static methods inside the same interface.**

# 6. Types of Interface Methods (After Java 9) —

|Method Type|Version Introduced|Method Having Body?|Default Type?|Overridable?|Who Can Call It?|
|---|---|---|---|---|---|
|**abstract**|Java 1|❌ No|✔ Yes (default method type)|✔ Yes|Implementing class|
|**default**|Java 8|✔ Yes|❌ No|✔ Yes|Through object / upcasting|
|**static**|Java 8|✔ Yes|❌ No|❌ No|InterfaceName.method()|
|**private**|Java 9|✔ Yes|❌ No|❌ No|Only inside interface|
