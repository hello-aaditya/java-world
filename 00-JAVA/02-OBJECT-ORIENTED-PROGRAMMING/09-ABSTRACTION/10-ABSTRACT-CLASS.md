# Abstract Class
> A class declared with the `abstract` keyword is known as an Abstract Class.

>It is a special type of class that cannot be used to create objects directly. Instead, it acts as a common blueprint for its sub-classes by defining the common properties and behaviors that they can inherit.

An Abstract Class can contain two types of methods:
1. Abstract Method
2. Concrete Method

### 1. Abstract Method
### 2. Concrete Method
## Syntax
```java
abstract class ClassName {

    // Fields
    private String field;

    // Constructor
    ClassName() {

    }

    // Concrete Method
    public void concreteMethod() {

    }

    // Abstract Method
    public abstract void abstractMethod();
}
```


## Rules

1. An abstract class is declared using the `abstract` keyword before the `class` keyword.
    
2. An abstract class **cannot be instantiated** directly.
    
    ```java
    Payment p = new Payment(); // Compile-time error
    ```
    
3. An abstract method has **no body** — only a declaration ending with a semicolon.
    
    ```java
    abstract void pay(double amount);
    ```
    
4. If a subclass extends an abstract class, it **must implement all abstract methods** of the parent — otherwise, the subclass itself must also be declared `abstract`.
    
5. An abstract class **can have constructors**. The constructor doesn't run on its own (since the class can't be instantiated), but it runs when a subclass object is created, via `super()`.
    
6. An abstract class **can have normal (concrete) methods**, instance variables, static methods, and constructors — it's not restricted to only abstract methods.
    
7. Abstract methods **cannot be `private`**, `static`, or `final`.
    
    - `private` → subclasses couldn't override it, defeating the purpose.
    - `static` → static methods belong to the class, not an instance, so they can't be overridden.
    - `final` → `final` means "cannot be overridden," which directly contradicts the purpose of an abstract method.
8. A class can be declared `abstract` even with zero abstract methods (covered earlier — used purely to prevent instantiation).
    
9. If a class contains even one abstract method, the class itself **must** be declared `abstract`.
    
10. An abstract class **can extend another abstract class** without implementing its abstract methods — the obligation to implement passes down until a concrete class picks it up.
    
