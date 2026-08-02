#### Parent Class
```java
class Program1 {
	Program1() {
		System.out.println("Program1 Constructor");
	}
}
```
#### Child Class
```java
class Program2 extends Program1 {
	Program2() {
		System.out.println("Program2 Constructor");
	}
}
```
#### Main Class
```java
public class Main {
	public static void main(String[] atgs) {
		Program2 p2 = new Program2();
	}
}
```
#### Output
```output
Program1 Constructor
Program2 Constructor
```

---
## Before Compilation
#### Parent Class
```java
class Parent {
	void disp1() {
		System.out.println("Inside disp1");
	}
}
```
#### Child Class
```java
class Child {
	void disp2() {
		System.out.println("Inside disp2");
	}
}
```
#### Main Class
```java
class Main {
	public static void main(String[] args) {
		Child c1 = new Child();

		c1.disp1();
		c1.disp2();
	}
}
```

## After Compilation
#### Parent Class
```java
class Object {
	// default constructor
	public Object() {
	}
}

class Parent {
	// default constructor
	public Parent() {
		super(); // sends control to Object class constructor
		System.out.println("Inside Parent class constructor");
	}

	void parentMethod() {
		System.out.println("Inside Parent class Method");
	}
}
```
#### Child Class
```java
class Child1 extends Parent {
	// default constructor
	public Child1() {
		super(); // sends control to Parent class constructor
		System.out.println("Inside Child1 class constructor");
	}

	void childMethod() {
		System.out.println("Inside Child class Method");
	}
}
```
#### Main Class
```java
class Main extends Object {
	// default constructor
	public Main() {
		super(); // calls Object class constructor
	}

	public static void main(String[] args) {
		Child1 c1 = new Child1();

		c1.parentMethod();
		c1.childMethod();
	}
}
```
#### Output
```markdown
Inside Parent class constructor
Inside Child1 class constructor
Inside Parent class Method
Inside Child class Method
```
### Step-by-Step Flow of Control
1. **Control** enters the program and starts searching for the `main()` method.  
    It finds it inside the `Main` class.
    
2. Inside `main()`, we write:
    ```java
    Child1 c1 = new Child1();
    ```
    As soon as the **control** finds the `new` keyword, a **block of memory** is created inside the **heap** for the object of `Child1`.
    
3. After that, the **control** encounters the `Child1()` constructor,  
    which means it is now calling the **constructor of the Child1 class**.
    
4.  Inside the `Child1` constructor, the **first line** is `super();`.  
    Whether you write it or not, the compiler automatically puts it there.  
    This `super()` is responsible for **sending the control to the parent class constructor**, i.e., to the **Parent class**.
    
5. Now, the **control** moves to the **Parent class**.  
    Inside the `Parent()` constructor, the first line is again `super();`  
    which means the **Parent class definitely has its own parent**, that is the **Object class**.
    
6. The **control** now goes to the **Object class** and enters the `Object()` constructor.  
    But since the `Object` constructor has nothing to execute,  
    control immediately **comes back** to the **Parent class**.
    
7. The **control** now executes the remaining statements of the **Parent constructor**,  
    prints `"Inside Parent class constructor"`,  
    and when the constructor ends, the **control** returns to the **Child1 constructor**.
    
8. The **control** now executes the remaining lines inside the **Child1 constructor**,  
    prints `"Inside Child1 class constructor"`,  
    and when it ends, the **control** comes back to the **Main class**.
    
9. By this time, the **object of Child1** is completely created in the heap.  
    The **address of that object** is now assigned to reference variable `c1`.
    
10. After that, the **control** continues its normal flow —  
    executing `c1.parentMethod()` and `c1.childMethod()`,  
    which print:
    ```java
    Inside Parent class Method
	Inside Child class Method
    ```

### How`super()` Works
- `super()` **always appears as the first line** inside a constructor.
    
- It is used to **call the parent class constructor**.
    
- If you don’t write it, Java **automatically adds it** to make sure the chain of constructors remains connected.
    

That’s why, even when we only create a **Child class object**,  
the **Parent constructor executes first**, followed by the **Child constructor**.

# Constructor Chaining
> The process of **connecting the child class constructor to the parent class constructor** using **`super()`** is called **Constructor Chaining**.

---
## Parameterized Constructor Chaining
## Example 1: Working Fine (Because Parent Has Default Constructor)
#### Parent Class
```java
public class Program1 {
	Program1() {
		System.out.println("Program1 Constructor");
	}
}
```
#### Child Class
```java
public class Program2 extends Program1 {
	Program2(int a) {
		System.out.println("Program2 Constructor");
	}
}
```
#### Main Class
```java
public class Main {
	public static void main(String[] args) {
		Program2 p2 = new Program2(20);
	}
}
```
#### Output
```markdown
Program1 Constructor
Program2 Constructor
```
### Explanation:
When we create an object of `Program2`,  
**control** first goes to the `Program2(int a)` constructor.

Inside the `Program2` constructor, the **first line** is `super();` (even though we didn’t write it, the compiler adds it automatically).

So, the **control goes upward** to the **parent class** — `Program1`.  
`Program1` has a **zero-parameter constructor**, so the control enters there, executes it, prints the message, and **comes back** to the `Program2` constructor.

That’s why the output shows:
```markdown
Program1 Constructor
Program2 Constructor
```

---
## Example 2: Error Case (Parent Has Only Parameterized Constructor)
#### Parent Class
```java
public class Program1 {
	Program1(int b) {
		System.out.println("Program1 Constructor");
	}
}
```
#### Child Class
```java
public class Program2 extends Program1 {
	Program2(int a) {
		super();  // ❌ this line will cause an error
		System.out.println("Program2 Constructor");
	}
}
```
#### Main Class
```java
public class Main {
	public static void main(String[] args) {
		Program2 p2 = new Program2(20);
	}
}
```
### Explanation:
When we write `Program2 p2 = new Program2(20);`,  
the **control goes** to the `Program2(int a)` constructor.

The very first line is `super();`, which means control **goes upward** to the **parent class** in search of a **zero-parameter constructor**.

But in the parent class, we only have:
```java
Program1(int b) { ... }
```
There is **no zero-parameter constructor**.  
So, the control **cannot find any matching constructor**,  
and that’s why the compiler shows an **error**.
## How to fix it
We must call the **parameterized constructor** of the parent class explicitly using `super(arguments)`.

#### Corrected Code
```java
public class Program2 extends Program1 {
	Program2(int a) {
		super(10); // now control goes to Program1(int b)
		System.out.println("Program2 Constructor");
	}
}
```
#### Output:
```markdown
Program1 Constructor
Program2 Constructor
```
#### Explanation of Control Flow

1. Control enters the `main()` method.
    
2. Finds the line `new Program2(20)` → creates memory for the object.
    
3. Control enters the `Program2(int a)` constructor.
    
4. The first line is `super(10);` → control **goes to parent class** `Program1(int b)`.
    
5. Executes parent’s constructor → prints `"Program1 Constructor"`.
    
6. Control **comes back** to `Program2(int a)` constructor.
    
7. Executes `"Program2 Constructor"`.
    
8. Control returns to the main method → object creation completed.
## Conclusion:
- If the parent has **only a parameterized constructor**,  
    and the child does not call it using `super(...)`, → **error**.
    
- The compiler never adds a default constructor automatically **if we already have a parameterized one**.
    
- To fix the error, either:
    
    - Create a zero-parameter constructor in the parent class, or
        
    - Call the existing parameterized constructor using `super(arguments)`.
