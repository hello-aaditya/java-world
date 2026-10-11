# Variable
A **Variable** is a name given to **memory address** to store our information that can be used and modify during program execution.
In Java, Variables are categorized on the basis of **where they are declared** & **how long they live**:
1. Local Variable
2. Instance Variable
3. Static Variable
	and one more 4. Reference Variable (Address Variable)
## 1. Local Variable
> A **local variable** is a variable declared **inside a method, constructor, or any block**.
- Local variables **exist only while** the method or block is executing and are **destroyed** automatically once the method completes execution.
- Local Variables are stored in the **stack memory**, inside the activation record of that method.
- Local Variables **don't receive default values**, so we **must initialize them explicitly** before using them otherwise we get compile-error.
**Example:**
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
## 2. Instance Variable (Class Variable)
> An **instance variable** is a variable declared **inside a class but outside any method**, **constructor**, and **block**. 
- Instance Variable is also known as **Class Variable**.
- Instance Variables **exist in the heap segment** as long as **the object exists in the stack segment**.
- Each object gets its own separate copy of instance variables, which are stored inside the **heap segment**.
- If not explicitly initialized, instance variables are automatically assigned **default values** (e.g., `0` for _int_, `null` for _String_, `false` for _boolean_, etc).
- Instance variables are also called **non-static member variables**.
**Example:**
```java
public class Employee {
    int id;           // instance variable
    String name;      // instance variable
    
    void work() {
        System.out.println("Working");
    }
}
```
Here, **`id`** and **`name`** are instance variables. When we create **`e1`** and **`e2`**, each object gets its **own copy** of **`id`** and **`name`** inside the **heap memory**, independent of one another.
## 3. Static Variable
> A **static variable** is a variable declared inside a class using the `static` keyword. It belongs to the **class itself**, not to any individual object.
- Static Variables are also known as **Class Variables**.
- No matter how many objects are created, **all objects share a single copy** of a static variable — there's only **one copy in memory**,
- Static Variables are stored in the **Method Area** (also called **Metaspace** in Java 8+).
- If not explicitly initialized, static variables are automatically assigned **default values**, just like instance variables (e.g., `0` for _int_, `null` for _String_, `false` for _boolean_).
- Static Variables are loaded into memory **once, when the class is loaded** by the JVM — even before any object is created — and they exist **as long as the class is loaded**.
- Since a static variable belongs to the class, it's typically accessed using the **class name** (`ClassName.variableName`), though accessing it via an object reference also works (not recommended).

#### 4. Reference Variables (Address variables)
> A **reference variable** is a variable that **stores the memory address (reference)** of an object that lives in the **heap memory**.
- Reference variables are also called **Address Variables**.
- Reference variables **do not hold the actual object**, they only hold the **address (reference)** of that object.
- Reference variables themselves are stored in the **stack memory**, inside the method or block where they are declared.
- A single class can have multiple reference variables pointing to **different objects** or even the **same object**.
[**PTO**](170-MEMORY-MANAGEMENT.md)