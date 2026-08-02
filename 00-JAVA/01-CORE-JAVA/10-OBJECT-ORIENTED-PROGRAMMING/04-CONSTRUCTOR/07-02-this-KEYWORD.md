# Default Constructor and `this` Keyword
**Class Program**
```java
class Program {
    int a, b;
}
```
**Program Objects:**
```java
class Main {
    public static void main(String[] args) {
        Program p1, p2, p3;

        p1 = new Program();
        p2 = new Program();
        p3 = new Program();
    }
}
```
##### Step-1: Control enters the `main()` method
When the JVM starts execution, it calls the `main()` method.  
At this point, the **activation record of `main()` is created inside the **stack segment**.
Inside it, three **reference variables** are declared:

```java
Program p1, p2, p3;
```

Each of them (p1, p2, p3) is created in the **stack**, but they don’t point anywhere yet.  
Right now, all three contain **null**.
##### Step-2: Line 4 → `p1 = new Program();`
**Now the interesting part starts:**
When the compiler sees the word `new`, it knows —

> “I have to create a new object inside the heap memory.”

**So what happens:**
- A small **block of memory** is created inside the **heap**.  
    Let’s say it gets address **0x1000**.
- The compiler looks for a **constructor** in the `Program` class.  
    But we didn’t write any constructor!

That’s okay —

> Java automatically provides a **default constructor** if we don’t create one.

---
### What is Default Constructor?

> A **default constructor** is a no-argument constructor that Java creates automatically if we don’t write any constructor in our class.

It looks like this (invisibly created by compiler):
```java
Program() {
    // empty body
}
```
This constructor runs automatically **when the object is being created**.

---
#### What Happens Inside the Default Constructor
When this default constructor runs, a **special reference variable** called **`this`** comes into play.
- The **`this` keyword** represents the **current object** that is being constructed or used.
- So, while this constructor is running for the first object,  
    `this` → points to the object at memory address **0x1000**.

Inside that object:
```java
a = 0
b = 0
```
(Default values are assigned automatically.)

After finishing the constructor, the control returns to `main()` again, and now:
**the control goes back to line 4.**  
Now the address `0x1000` (of the newly created object) is assigned to `p1`.

So now:  
`p1` → `0x1000`  
`this` (which was pointing to 0x1000 inside constructor) is **gone** because constructor execution is finished.
##### Step-3: Line 5: `p2 = new Program();`
**Same story again —**
- `new` creates another block of memory in heap, say **0x2000**.
- Default constructor runs again.
- `this` now points to this **new object (0x2000)**.
- Inside it, variables `a` and `b` get default values (0, 0).
- Constructor finishes → `p2` gets 0x2000.
##### Step-4: Line 6: `p3 = new Program();`
- A third block of memory is created → **0x3000**.
- `this` now points to **0x3000** (the new object).
- Default constructor initializes its variables (a=0, b=0).
- Then `p3` receives address **0x3000**.
##### Step-5: Assigning Values
Now when we write:
```java
p1.a = 10;
p1.b = 20;
```
The control looks at the address stored in `p1` (0x1000) and sets:
```java
a = 10, b = 20
```
inside the heap block at 0x1000.

Similarly:
```java
p2.a = 30; p2.b = 40;
p3.a = 50; p3.b = 60;
```
update their own respective heap blocks (0x2000 and 0x3000).
##### Step-6: End of Execution
When `main()` completes:
- The **activation record of `main()`** is removed from the stack.
- All local references (`p1`, `p2`, `p3`) are destroyed.
- The heap objects (`0x1000`, `0x2000`, `0x3000`) become **unreachable**, and the **Garbage Collector** will clean them later.
![`this` keyword](./images/thisKeyword.drawio.svg)

---
## Understanding `this` Keyword Through Example
```java
package oops.constructor;

public class ThisClass {
	int a;
	int b;
	
	void display() {
		System.out.println(this);
	}
}
```

```java
package oops.constructor;

public class ThisObject {
	public static void main(String[] args) {
		ThisClass t1 = new ThisClass();
		
		System.out.println(t1);
		t1.display();
	}
}
```
1. Inside the `main()` method,  
	we create an object:
	```java
	ThisClass t1 = new ThisClass();
	```
	This means:
	- A new object of `ThisClass` is created in **heap memory**.
	- Its reference (memory address) is stored in `t1` (in the stack).
2. Then we print:
	```java
	System.out.println(t1);
	```
	This prints something like:
	```java
	oops.constructor.ThisClass@372f7a8d
	```
	This is the **memory reference** (address) of the object.  
	It tells where the object actually exists in heap memory.
3. Next, we call:
	```java
	t1.display();
	```
	Inside `display()`, we again print:
	```java
	System.out.println(this);
	```
	Here, `this` represents the **same object** that called the `display()` method —  
	in this case, the object referred by `t1`.
	
	So it will print **the same address** as the previous one:
	```java
	oops.constructor.ThisClass@372f7a8d
	```
#### Observation
Both print statements show the **same memory address**.  
That means —

> `this` and the reference variable (`t1`) both refer to the **same object** in memory.

#### Conclusion
> `this` keyword refers to the **current object** — i.e., the object through which the method is called.

So, in this example:
- `t1` → object reference in main method.
- `this` → same object reference, but used **inside the class**.

They both point to the **same object in heap memory**.

---
