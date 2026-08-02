
![Class & Object: Memory: Prospective](00-JAVA/01-CORE-JAVA/10-OBJECT-ORIENTED-PROGRAMMING/00-INTRODUCTION-TO-OOP/images/memory_management_Employee.drawio.svg)
# Flow of Memory in Java (Objects, Stack, Heap)

### 1. **Class Definition**
```JAVA
public class Employee {
	int id;
	String name;
	void work() {
		System.out.println("Working");
	}
}
```
- A **class** is just a **blueprint/template**.
- At this stage, **no memory is allocated** for variables (`id`, `name`) or methods.
- Memory is only allocated **when an object is created**.
### 2. **Object Creation (Instantiation)**
```JAVA
public class EmployeeObject {
	public static void main(String[] args) {
	
		Employee e1 = new Employee();
		e1.id = 11;
		e1.name = "Ajay";
		e1.work();
		
		Employee e2 = new Employee();
		e2.id = 22;
		e2.name = "Kumar";
		e2.work();
	}
}
```

```JAVA
Employee e1 = new Employee();
```
- `new Employee()` → Creates a **new object** in **Heap Memory**. 
- `e1` → A **reference variable**, stored in **Stack Memory**, pointing to that object.
### 3. **Stack Segment (Method Calls + References)**
- Stores:
    - **Method calls** (activation records).
    - **Reference variables** (`e1`, `e2`).
- Reference variable doesn’t store the object directly. Instead, it stores a **memory address** (like `0x7ffe5367e044` in the diagram). that's why a Reference Variable is also known as **Address Variable**.
### 4. **Heap Segment (Objects)**
- Stores actual **objects** created by `new`.
- Each object has its own **copy of instance variables**.
- **Example:**
    - `e1` points to an object with `{id=11, name="Ajay"}`.
    - `e2` points to another object with `{id=22, name="Kumar"}`.
### 5. Flow in My Code
```JAVA
Employee e1 = new Employee();   // Object created in heap, ref in stack
e1.id = 11;                     // Stored inside heap object
e1.name = "Ajay";               // Stored inside heap object
System.out.println(e1.id);      // JVM looks at stack ref → goes to heap → prints 11
System.out.println(e1.name);    // Prints "Ajay"
e1.work();                      // Calls work() method, activation record on stack
```
Now second object:
```JAVA
Employee e2 = new Employee();   // Another object created in heap
e2.id = 22;
e2.name = "Kumar";
```
- Both `e1` and `e2` live in **stack**, pointing to **different objects** in heap.
- That’s why changing `e1.name` doesn’t affect `e2.name`.
### 6. Diagram Explanation
As soon as we run the program that has the `main()` method, JVM sends its control to the `main()` method.

The very next line has a statement with `=`, so first it goes to the RHS. The very first word on the RHS is `new`. As soon as JVM gets the `new` keyword, it creates a block of memory inside the **heap** and provides an address (suppose **0x7ffe5367e044**) to this block of memory. 
**But whom does it ask for `new`?** 
It asks the `Employee()` class. JVM immediately sends its control to the Employee class.

As JVM enters the Employee class:

**First line** – it has `int id`. JVM allocates memory inside address **0x7ffe5367e044** for `id` and initializes it with the default value, which is **0**.

**Next line** – it has `String name`. JVM allocates memory inside address **0x7ffe5367e044** for `name` and initializes it with the default value, which is **null**.

**Next** – `work()` method is defined. The method code is stored in the **method area** (not inside the object), and all Employee objects will share this same method.
> **Note:** In the diagram above, `work(){}` is shown inside each heap object for visualization purposes only. In reality, the method exists **once** in the Method Area, and both `e1` and `e2` share the same method code.

Now JVM reaches the end of the Employee class, and it returns back to the place where it came from – inside the `main()` method.

Now JVM comes to the LHS part of the `=` and gives the address of the memory block to object **e1**, which is of type Employee. The object `e1` is stored in the **stack segment**, and it holds the reference **0x7ffe5367e044** (pointing to the heap memory).

**Next line:** `e1.id = 11`  
Object `e1` is pointing to address **0x7ffe5367e044**. JVM goes to `id` at that location and updates the value from **0** to **11**.

**Next line:** `e1.name = "Ajay"`  
Object `e1` is pointing to address **0x7ffe5367e044**. The string `"Ajay"` is created in the **String Pool** (let's say at address **5000**). JVM goes to `name` at address **0x7ffe5367e044** and updates the value from **null** to **5000** (the reference to "Ajay").

**Next line:** `e1.work()`  
JVM invokes the `work()` method. An **activation record** for `work()` is created on the stack, and the method executes (prints "Working"). Once done, the activation record is removed from the stack.

---

## Now for the second object (e2):

**Next line:** `Employee e2 = new Employee();`

Again, JVM sees the `=` and moves to the RHS. It encounters the `new` keyword, so it creates **another block of memory** in the heap with a new address (suppose **0x7ffe5367e599**). JVM sends its control to the `Employee()` class again.

Inside the Employee class:

**First line** – `int id`. JVM allocates memory inside address **0x7ffe5367e599** for `id` and initializes it with **0**.

**Next line** – `String name`. JVM allocates memory inside address **0x7ffe5367e599** for `name` and initializes it with **null**.

The `work()` method already exists in the method area, so nothing new happens here.

JVM returns to the `main()` method.

Now JVM comes to the LHS of `=` and gives the address **0x7ffe5367e599** to object **e2**, which is stored in the **stack segment**.

**Next line:** `e2.id = 22`  
Object `e2` is pointing to address **0x7ffe5367e599**. JVM goes to `id` at that location and updates the value from **0** to **22**.

**Next line:** `e2.name = "Kumar"`  
Object `e2` is pointing to address **0x7ffe5367e599**. The string `"Kumar"` is created in the **String Pool** (let's say at address **6000**). JVM goes to `name` at address **0x7ffe5367e599** and updates the value from **null** to **6000** (the reference to "Kumar").

**Next line:** `e2.work()`  
JVM invokes the `work()` method. An **activation record** for `work()` is created on the stack for this call, the method executes (prints "Working"), and then the activation record is removed.

---
**Program Termination:**
Once all the statements inside `main()` are executed, the program ends. At this point, the **activation record for `main()` method** (where `e1` and `e2` were stored) gets deleted from the stack segment.

Now, no one is pointing to the addresses **0x7ffe5367e044** and **0x7ffe5367e599** in the heap. These objects become **garbage objects**.

The **Garbage Collector (GC)** is responsible for automatically de-allocating the memory occupied by these unreachable objects (**0x7ffe5367e044** and **0x7ffe5367e599**).

[**PTO**](20-JAVA-VARIABLES.md)