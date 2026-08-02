We know that **any word followed by parentheses `()`** is considered a **method** in java.
Example:
```java
display();
calculate();
```
So when we write:
```java
Student s1 = new Student();
```
Then a question arises 👇

> **1.**  If it’s a method, where is it defined in the class?  
> **2.**  And if not defined, why doesn’t the compiler show an error?

---
# Invalid State
When we create an object like this:
```java
Student s1 = new Student();
```
All the properties of the object get their **default values**.
![Invalid State](invalidState.drawio.svg)
![Memory: Invalid State](invalidStateMemory.drawio.svg)

That’s an **invalid state** — because a student cannot have an age of `0` or a name as `null`.  
Ideally, when we create an object, it should already be in a **valid state**.
The Solution  is- Constructor

---
# CONSTRUCTOR
**Definition:**
> **Constructor** is a _special method_ which gets called automatically during the **construction of an object**.

## Properties
- The constructor name must be **exactly same as the class name**.
- By default, a constructor is of **public type**.
- A constructor **can take values (parameters)** during object creation to set the initial data.
- The constructor **must not have any return type** (not even `void`).
### Example:
**Student class**
```java
package oops.constructor;

public class Student {
    int age;
    double height;
    String name;

    // Constructor
    public Student(int a, double h, String n) {
        age = a;
        height = h;
        name = n;
    }

    public void display() {
        System.out.println("Age: " + age);
        System.out.println("Height: " + height);
        System.out.println("Name: " + name);
    }
}
```
Student Object
```java
package oops.constructor;

public class StudentDemo {
    public static void main(String[] args) {
        Student s1 = new Student(15, 5.5, "Ajay");
        s1.display();
    }
}
```
![Valid State](constructorValidStateMemory.drawio.svg)
# Difference between Method and Constructor
| #   | **Method**                                                                                   | **Constructor**                                                                 |
| --- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| 1.  | A method is used to **define the behavior** or perform some specific task of the object.     | A constructor is used to **initialize the object** at the time of its creation. |
| 2.  | A method can have **any name** (not related to the class name).                              | The constructor name must be **exactly same as the class name**.                |
| 3.  | A method **must have a return type** (it can be `void` or any other data type).              | A constructor **has no return type**, not even `void`.                          |
| 4.  | A method is **called manually** using the object.                                            | A constructor is **called automatically** when the object is created.           |
| 5.  | A method is mainly used to **perform operations** or **actions** on already created objects. | A constructor is mainly used to **set the initial values** of the object.       |
| 6.  | Methods can be **inherited** and **overridden**.                                             | Constructors are **not inherited**, but they **can be overloaded**.             |
| 7.  | A method can be called **many times** using the same object.                                 | A constructor is called **only once** — at the time of object creation.         |
| 8.  | Syntax example: `obj.display();`                                                             | Syntax example: `Student s1 = new Student();`                                   |

![Object-Creation](createAnObject.drawio.svg)
