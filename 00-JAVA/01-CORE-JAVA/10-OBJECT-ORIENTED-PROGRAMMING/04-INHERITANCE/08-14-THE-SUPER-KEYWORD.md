# The `super` Keyword in Java
> The `super` keyword in Java is a **reference variable** that is used to refer to the **immediate parent class object**.  
> 
It comes into the picture whenever both parent and child classes have the **same variable names**, **same method names**, or when the **child wants to call the parent’s constructor**.

## It is mainly used in three cases:

1. To call **parent class constructor**
2. To access **parent class variable**
3. To access **parent class method**
## 1. `super()` in Constructors
> The keyword `super()` is used to **call the constructor of the immediate parent class**.
>
It must always be written in the **first line** of the child class constructor.
### Example 1 — Implicit `super()`
#### Parent Class
```java
public class Parent {
	Parent() {
		System.out.println("Inside Parent Constructor");
	}
}
```
#### Child Class
```java
public class Child extends Parent {
	Child() {
		System.out.println("Inside Child Constructor");
	}
}
```
#### Main Class
```java
public class Main {
	public static void main(String[] args) {
		Child c = new Child();
	}
}
```
#### Output
```markdown
Inside Parent Constructor
Inside Child Constructor
```
### Explanation
Even though we didn’t write `super()` inside the child constructor,  
Java **automatically inserted** it like this:
```java
Child() {
	super();  // inserted by compiler
	System.out.println("Inside Child Constructor");
}
```
So when control creates the object `new Child()`:
1. Control goes to the **Child class constructor**.
2. The **first line** is `super()`, so control jumps to the **Parent class constructor**.
3. The **Parent constructor** executes completely.
4. Then control **returns back** to the **Child constructor**, and executes the remaining statements.

That’s why in output, the **Parent constructor message appears first**, then the **Child’s**.
### Example 2 — Explicit `super()` with Parameterized Constructor
We can also use `super()` to **pass arguments** to the parent class constructor.
#### Parent Class
```java
public class Parent {
	Parent(int x) {
		System.out.println("Inside Parent Constructor, value: " + x);
	}
}
```
#### Child Class
```java
public class Child extends Parent {
	Child() {
		super(100); // calling Parent(int) constructor explicitly
		System.out.println("Inside Child Constructor");
	}
}
```
#### Main Class
```java
public class Main {
	public static void main(String[] args) {
		Child c = new Child();
	}
}
```
#### Output
```markdown
Inside Parent Constructor, value: 100
Inside Child Constructor
```
### Explanation
Here, we wrote `super(100)` inside the child constructor —  
this means we are **manually calling the parent’s parameterized constructor** and passing `100` as an argument.
So during execution:
1. Control enters `Child()` constructor.
2. Finds `super(100)` → control jumps to `Parent(int x)` constructor.
3. Executes parent’s constructor → prints its message.
4. Returns back to child constructor → executes its remaining lines.
---
## 2. `super` with Variables
If we use `super` with a variable inside the child class,  
then the **control goes to the immediate parent class** and fetches the value of that variable.
#### Parent Class
```java
public class Parent {
	int a = 10;
	void display() {
		System.out.println("Inside Parent class and display Method");
		System.out.println("The value of a is: " + a);
	}
}
```
#### Child Class
```java
public class Child extends Parent {
	int a = 20;   // same variable name as in parent
	
	@Override
	void display() {
		System.out.println("Inside Child class and display Method");
		System.out.println("The value of a is: " + super.a);
	}
}
```
#### Main Class
```java
public class Main {
	public static void main(String[] args) {
		Parent p = new Parent();
		p.display();
		
		Child c = new Child();
		c.display();
	}
}
```
#### Output
```markdown
Inside Parent class and display Method
The value of a is: 10
Inside Child class and display Method
The value of a is: 10
```
### Explanation
Here, both the parent and child have a variable named `a`.  
Normally, when we use `a` inside the child class, it refers to the **child’s variable**.  
But if we want to access the **parent’s version of `a`** then we use `super.a`.

So,
- `a` → refers to child variable (value 20)
- `super.a` → refers to parent variable (value 10)

That’s why in output, we can see the value `10` fetched from the parent class.
## 3. `super` with Methods
If we use `super` with a method inside the child class,  
then the **control goes to the immediate parent class** and executes the method written there.
#### Parent Class
```java
public class Parent {
	int a = 10;
	void display() {
		System.out.println("Inside Parent class and display Method");
		System.out.println("The value of a is: " + a);
	}
}
```
#### Child Class
```java
public class Child extends Parent {
	int a = 20;
	
	@Override
	void display() {
		System.out.println("Inside Child class and display Method");
		super.display();  // calls parent class method
		System.out.println("The value of a is: " + a);
	}
}
```
#### Main Class
```java
public class Main {
	public static void main(String[] args) {
		Parent p = new Parent();
		p.display();
		
		Child c = new Child();
		c.display();
	}
}
```
#### Output
```markdown
Inside Parent class and display Method
The value of a is: 10
Inside Child class and display Method
Inside Parent class and display Method
The value of a is: 10
The value of a is: 20
```
### Explanation
1. When the control calls `c.display()`, it goes to the **child class method** first.
2. Inside that, we find `super.display()`, so control moves upward to the **parent class** and executes its `display()` method.
3. After finishing the parent’s method, control comes back to the **child method** and executes the remaining lines.

So the order of execution becomes:
- Parent’s method first (because of `super.display()`)
- Then child’s method continues.

That’s why we see both the messages — parent’s and child’s — in the output.