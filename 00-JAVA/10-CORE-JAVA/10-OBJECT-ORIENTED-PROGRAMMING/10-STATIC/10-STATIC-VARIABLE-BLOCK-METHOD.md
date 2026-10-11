# `static` keyword in Java
> When a **member** (variable, method, or block) of a class is declared using the keyword `static`,  then that member is called a **static member**.
> 
> A **static member** **belongs to the class itself**, not to any specific object of the class. means it is **common for all objects** of that class — there is only **one copy** of it in memory.

#### Usage
- The `static` keyword is mainly used for **memory management**.
- It allows us to create **class-level variables, methods, and blocks** that can be accessed **without creating an object**.
## 1. Static Variable
> Inside a class, if a variable is declared with the `static` keyword, then it is known as **static variable**. 
- **Static Variable** is also known as **Class Variable**.
```java
static int a;
static int b;
```
## 2. Static Method
> Inside a class, if a method is declared with the `static` keyword, then it is known as a **static method**.
```java
static void display() {
    System.out.println("Static Method");
}
```
- A Static Method is also known as **Class Method** or **Class Level Method**. 
- Static methods belong to the **class** rather than an object.
- Static methods **without creating an object**.
- A Static method **can access only static members** (static variables, other static methods).
##### Example:
```java
class Demo {
    static void show() {
        System.out.println("Static Method Executed");
    }

    public static void main(String[] args) {
        Demo.show(); // no object required
    }
}
```
## 3. Static Block
> Inside a class, if a block is declared with the `static` keyword, then it is known as a **static block**.
```java
static {
    System.out.println("Static Block Executed");
}
```
- A **Static Block** is also known as **class-level block**.
- A static blocks run **only once**, when the **class is loaded into memory**.
- A **static block** is used to **initialize static variables** or **execute setup code** before any object is created.
# Non-Static in Java
|        Type         |     Example      |   Also Known As   |
|:-------------------:|:----------------:|:-----------------:|
| Non-static variable |     `int a;`     | Instance Variable |
|  Non-static method  | `void getData()` |  Instance Method  |
|  Non-static block   |    `{ ... }`     |  Instance Block   |

