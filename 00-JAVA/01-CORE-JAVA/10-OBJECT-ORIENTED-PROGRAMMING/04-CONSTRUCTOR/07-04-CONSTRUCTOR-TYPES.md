# Constructor Types
There are two types of constructor-
1. Default Constructor
2. Parameterized Constructor
## 1. Default Constructor (Zero-Parameterized Constructor)
> A **default constructor** is a constructor that accepts **no-argument (Parameters) and that is **automatically provided by the Java compiler** if no constructor is written in the class.

### Meaning in Simple Words
If we create a class but don’t write any constructor,  
Java **automatically creates one** behind the scenes —  
so that object creation can still happen without errors.

This default constructor helps the **object to be created in a valid state**,  
even if we haven’t initialized anything manually.

---
#### Example-1: No Constructor Written
```java
class Student {
    int roll;
    String name;
    double percentage;
}
```
Here, we didn’t write any constructor.  
Now when we create an object:
```java
Student s1 = new Student();
```
The question is —

> How is this object getting created when there is no constructor defined?

**The answer is-**
Java **compiler automatically provides** a **default constructor** during compilation.
### How Default Constructor Looks (Internally)
```java
Student() {
    
}
```
Here:
- `Student()` → constructor with no parameters.
  Every class in Java inherits from `Object`, so this call happens automatically.
    
This constructor doesn’t initialize any values —  
it only calls the parent class constructor to complete object construction.

---
#### Example 2 — Demonstrating the Default Constructor
```java
class Student {
    int roll;
    String name;
    double percentage;

    void disp() {
        System.out.println("Roll: " + roll);
        System.out.println("Name: " + name);
        System.out.println("Percentage: " + percentage);
    }
}

public class Demo {
    public static void main(String[] args) {
        Student s1 = new Student();  // default constructor called
        s1.disp();
    }
}
```
```output
Roll: 0
Name: null
Percentage: 0.0
```

![Default Constructor](defaultConstructor.png)
#### Example 3 — Manually Creating a Default Constructor
We can also **manually create** a default constructor in our class,  
especially when we want to print something or initialize basic values.
```java
class Student {
    int roll;
    String name;
    double percentage;

    // Manually created default constructor
    Student() {
        System.out.println("Default constructor called!");
        roll = 101;
        name = "Ajay";
        percentage = 90.0;
    }

    void disp() {
        System.out.println("Roll: " + roll);
        System.out.println("Name: " + name);
        System.out.println("Percentage: " + percentage);
    }
}
```

```java
public class Demo {
    public static void main(String[] args) {
        Student s1 = new Student();
        s1.disp();
    }
}
```

```output
Default constructor called!
Roll: 101
Name: Ajay
Percentage: 90.0
```
Now, the constructor initializes the object with our given values instead of default ones.
## Key Points About Default Constructor
| Concept                           | Description                                                                  |
|:--------------------------------- |:---------------------------------------------------------------------------- |
| Created by                        | **Compiler** (not JVM)                                                       |
| When created                      | Only when **no other constructor** is written in the class                   |
| Type                              | **No-argument** constructor                                                  |
| Purpose                           | To allow object creation and call parent constructor                         |
| Default values                    | It initializes variables with **default values** (0, 0.0, null, false, etc.) |
| If you write your own constructor | The compiler **does not** provide a default one anymore                      |
| Can be written manually           | Yes, if you want to add logic or print messages                              |

---
---
## 2. Parameterized Constructor
> A **Parameterized Constructor** is a constructor that **accepts arguments (parameters)** while creating an object, in order to **initialize the object with specific values**.

### Meaning in Simple Words
In a **default constructor**, we don’t pass any value —  
so all variables either get default values or the ones we set manually inside it.

But in a **parameterized constructor**,  
we **pass the values** during object creation,  
so each object can have its **own unique data**.

---
#### Example-1:
```java
class Student {
    int roll;
    String name;
    double percentage;

    // Parameterized constructor
    Student(int roll, String name, double percentage) {
        this.roll = roll;
        this.name = name;
        this.percentage = percentage;
    }

    void disp() {
        System.out.println("Roll: " + roll);
        System.out.println("Name: " + name);
        System.out.println("Percentage: " + percentage);
    }
}
```

```java
public class Demo {
    public static void main(String[] args) {
        Student s1 = new Student(101, "Ajay", 90.5);
        Student s2 = new Student(102, "Rahul", 85.0);

        s1.disp();
        s2.disp();
    }
}
```

```output
Roll: 101
Name: Ajay
Percentage: 90.5

Roll: 102
Name: Rahul
Percentage: 85.0
```

![Parameterized Constructor](parametrized_constructor.png)
#### Explanation
- When the control executes
    ```java
    new Student(101, "Ajay", 90.5);
    ```
    
    it calls the **constructor** which has **three parameters** — `int`, `String`, and `double`.
    
- The values are passed directly from object creation to the constructor parameters.
- These parameters are then **assigned to instance variables**, so each object gets its own data.

---
#### ⚠️ Note About Default Constructor

Once we write any **constructor manually**,  
-> the **compiler stops creating the default constructor automatically**.

So in the above example, if we try to create an object like:
```java
Student s3 = new Student();
```

we’ll get a **compile-time error**,  
because the **default (no-argument) constructor** no longer exists.

---
#### Example-2: Adding Back a Default Constructor
```java
class Student {
    int roll;
    String name;
    double percentage;

    // Default constructor
    Student() {
        System.out.println("Default constructor called!");
    }

    // Parameterized constructor
    Student(int roll, String name, double percentage) {
        this.roll = roll;
        this.name = name;
        this.percentage = percentage;
    }
}
```

```java
Student s1 = new Student(); // calls default constructor
Student s2 = new Student(101, "Ajay", 90.5); // calls parameterized
```

## Key Points About Parameterized Constructor
| Concept             | Description                                                           |
| ------------------- | --------------------------------------------------------------------- |
| Definition          | Constructor with parameters to initialize object with given values    |
| Purpose             | To assign unique data to each object during creation                  |
| Called when         | We pass arguments while creating the object                           |
| Default constructor | Automatically removed if any constructor is written                   |
| Can be overloaded   | Yes, multiple constructors with different parameter lists are allowed |