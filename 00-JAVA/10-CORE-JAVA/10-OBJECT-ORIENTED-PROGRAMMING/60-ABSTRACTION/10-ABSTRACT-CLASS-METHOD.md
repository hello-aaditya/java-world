# Abstract Class
> An Abstract Class is a special type of class that cannot be instantiated and is declared using the `abstract` keyword. It is designed to be extended by subclasses, which provide concrete implementations for its abstract methods.
>
An abstract class can contain both abstract methods (methods without a body) and concrete methods (methods with a body), where abstract methods provide mandatory contracts and concrete methods provide shared and reusable logic for its subclasses.
>
Abstract classes are typically used when multiple related classes share a common base but differ in how they implement certain behaviors.
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

#### Cluster 1: Declaration & Instantiation

1. An abstract class is declared using the `abstract` keyword before the `class` keyword.
2. An abstract class cannot be instantiated directly.

```
Payment p = new Payment(); // Compile-time error
```

#### Cluster 2: Abstract Method Mechanics

1. An abstract method has no body — only a declaration ending with a semicolon.

```
abstract void pay(double amount);
```

2. Abstract methods cannot be `private`, `static`, or `final`.

- `private` → subclasses couldn't override it, defeating the purpose.
- `static` → static methods belong to the class, not an instance, so they can't be overridden.
- `final` → final means "cannot be overridden," which directly contradicts the purpose of an abstract method.

#### Cluster 3: Class ↔ Method Obligation

1. If a subclass extends an abstract class, it must implement all abstract methods of the parent — otherwise, the subclass itself must also be declared abstract.
2. A class can be declared abstract even with zero abstract methods (covered earlier — used purely to prevent instantiation).
3. If a class contains even one abstract method, the class itself must be declared abstract.
4. An abstract class can extend another abstract class without implementing its abstract methods — the obligation to implement passes down until a concrete class picks it up.

#### Cluster 4: Constructors & Other Members

1. An abstract class can have constructors. The constructor doesn't run on its own (since the class can't be instantiated), but it runs when a subclass object is created, via `super()`.
2. An abstract class can have normal (concrete) methods, instance variables, static methods, and constructors — it's not restricted to only abstract methods.
    
---
## Abstract Method
> A method which is declared using **`abstract`** keyword is known as **Abstract Method**. It contains only the method signature and **must be implemented by first concrete subclass**, (if and only if subclass is not abstract).

### Rules-
1. Abstract Method contains no method body.
2. since it has no method body therefore it ends with a semicolon (`;`).
3. It is declared using `abstract` keyword.
4. An Abstract Method can exist only inside an **abstract class** or an **interface**.
5. An Abstract Method forces subclasses to provide its own implementation.
### Syntax
```java
abstract returnType methodName(parameters);
```
## Concrete Method
> A **concrete method** is a method that **contains both method signature and the method body**.
> A concrete method defines **how a task is performed**, and subclasses can either use it- as it is or can override it (if it allowed).

### Rules-
1. Concrete Method contains a method body.
2. A Concrete Method can exist in regular classes and abstract classes but in Interfaces, only **`default`**, **`static`**, and **`private`** methods can be concrete.
3. A Concrete Method can be invoked directly when accessible.
### Syntax
```java
returnType methodName(parameters) {
    // method body
}
```