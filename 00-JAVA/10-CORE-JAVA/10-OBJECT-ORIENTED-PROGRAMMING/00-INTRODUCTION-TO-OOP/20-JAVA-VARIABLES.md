# Instance Variable (Class Variables)
> An **instance variable** is a variable declared **inside a class but outside any method**, **constructor** and **block**. 
> 
> It belongs to an object (*instance*) of that class.

- Instance Variables are also known as **Class Variables**.
- Each objects get its own separate copy of instance variables, which are stored inside **heap segment**.
- If not explicitly initialized, instance variables are automatically assigned **default values** (e.g., `0` for _int_, `null` for _String_, `false` for _boolean_ etc).
- Instance Variables **exist in the heap segment** as long as **the objects exists in the stack segment**. 
- Instance variables are also called as **non-static member variables**.
```java
public class Employee {
    int id;           // instance variable
    String name;      // instance variable
    
    void work() {
        System.out.println("Working");
    }
}
```
Here, **`id`** and **`name`** are instance variables. 
When we create **`e1`** and **`e2`**, each objects get its **own copy** of **`id`** and **`name`** inside the **heap memory**, independent of one another.
# Local Variable
> A **local variable** is a variable declared **inside a method, constructor, or block**.

- Local Variables are stored in the stack memory, inside the activation record of that method.
- Local Variables **don’t receive default values**, so we **must initialize them explicitly** before using them.
- Local variables **exist only while** the method or block is executing and are **destroyed** automatically once the method completes execution.

```java
public class Employee {
    int id;  // instance variable
    
    void work() {
        String task = "Coding";  // local variable
        System.out.println(task);
    }
    
    public static void main(String[] args) {
        Employee e1 = new Employee();  // e1 is a local variable
        e1.id = 11;
        e1.work();
    }
}
```

---
## Example: Local Variables & Instance Variables
```java
public class Employee {
    int id;           // instance variable
    String name;      // instance variable
    
    // Constructor
    Employee() {
        int defaultId = 100;        // local variable
        String defaultName = "New Employee";  // local variable
        
        this.id = defaultId;
        this.name = defaultName;
        
        System.out.println("Employee created with default values");
    }
    
    // Parameterized Constructor
    Employee(int empId, String empName) {
        int bonus = 5000;           // local variable inside constructor
        
        this.id = empId;
        this.name = empName;
        
        System.out.println("Bonus for new employee: " + bonus);
    }
}

public class Main {
    public static void main(String[] args) {
        Employee e1 = new Employee();           // calls first constructor
        Employee e2 = new Employee(22, "Kumar"); // calls second constructor
    }
}
```
##### Output:
```output
Employee created with default values
Bonus for new employee: 5000
```

Static Variable
> Inside a class, if a variable is declared with the `static` keyword, then it is known as **static variable**. 
- **Static Variable** is also known as **Class Variable**.
```java
static int a;
static int b;
```
## Quick Comparison: Instance Variable vs Local Variable
|     **Feature**     |                   **Instance Variable**                    |              **Local Variable**               |
|:-------------------:|:----------------------------------------------------------:|:---------------------------------------------:|
|    **Declared**     | Inside class, but outside methods, constructors, or blocks |    Inside a method, constructor, or block     |
| **Memory Location** |                  Heap (inside the object)                  | Stack (inside the method’s activation record) |
|  **Default Value**  |           Yes (e.g., `0`, `null`, `false`, etc.)           |      No (must be explicitly initialized)      |
|    **Lifetime**     |                As long as the object exists                |   Only during the method or block execution   |
|      **Scope**      |          Throughout the class (using the object)           |        Limited to the method or block         |
|     **Access**      |             Accessed using `this.variableName`             |      Accessed directly by variable name       |
# Reference Variables (Address Variables)
> A **reference variable** is a variable that **stores the memory address (reference)** of an object that lives in the **heap memory**.

- Reference variables are also known as **Address Variables**.
- Reference variables **do not hold the actual object**, they only hold the **address (reference)** of that object.
- Reference variables themselves are stored in the **stack memory**, inside the method or block where they are declared.
- A single class can have multiple reference variables pointing to **different objects** or even the **same object**.

[**PTO**](30-NORMAL-ANONYMOUS-GARBAGE-OBJECTS.md)