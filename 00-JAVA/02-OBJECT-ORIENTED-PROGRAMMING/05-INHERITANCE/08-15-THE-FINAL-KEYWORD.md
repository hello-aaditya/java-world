# The `final` keyword
> In Java, the `final` keyword is used to create constants or to restrict modification.

## It can be applied to **variables**, **methods**, **classes**.
- When a **variable** is declared final, its value cannot be changed.
- When a **method** is declared final, it cannot be overridden by any subclasses.
- When a **class** is declared final, it cannot be inherited by another class.
## 1. `final` with Variables
#### Parent Class
```java
public class Parent {
	final int value = 100; // final variable

	void showValue() {
		System.out.println("Parent value: " + value);
	}
}
```
#### Child Class
```java
public class Child extends Parent {
	void changeValue() {
		// value = 200; // ❌ Error: cannot assign a value to final variable 'value'
		System.out.println("Child cannot modify final variable");
	}
}
```
#### Main Class
```java
public class Main {
	public static void main(String[] args) {
		Child c = new Child();
		c.showValue();
		c.changeValue();
	}
}
```
#### Output
```markdown
Parent value: 100
Child cannot modify final variable
```
#### Explanation
- In the **Parent class**, the variable `value` is declared `final`.
- Once it is assigned a value (`100`), it **cannot be changed later**.
- If the child class tries to modify it, the compiler gives an **error**.
---
## 2. `final` with methods
#### Parent Class
```java
public class Parent {
	final void display() {
		System.out.println("This is a final method from Parent class");
	}
}
```
#### Child Class
```java
public class Child extends Parent {
	// ❌ Error: cannot override final method from Parent
	// @Override
	// void display() {
	//     System.out.println("Trying to override final method");
	// }
	
	void childMethod() {
		System.out.println("Child class own method");
	}
}
```
#### Main Class
```java
public class Main {
	public static void main(String[] args) {
		Child c = new Child();
		c.display(); // calling parent's final method
		c.childMethod();
	}
}
```
#### Output
```markdown
This is a final method from Parent class
Child class own method
```
#### Explanation
- The **display()** method in the parent class is marked as `final`.
- The child class can use it (it’s inherited), but it **cannot override** it.
- If we try to redefine it inside the child, the compiler will show an **error**.
---
## 3. `final` with class
#### Parent Class
```java
final class Parent {
	void show() {
		System.out.println("Inside final Parent class method");
	}
}
```
#### Child Class
```java
// ❌ Error: cannot inherit from final Parent
// public class Child extends Parent {
//     void show() {
//         System.out.println("Trying to inherit from final class");
//     }
// }
```
#### Main Class
```java
public class Main {
	public static void main(String[] args) {
		Parent p = new Parent();
		p.show();
	}
}
```
#### Output
```markdown
Inside final Parent class method
```
#### Explanation
- The class **Parent** is declared as `final`.
- So it **cannot be extended** or inherited by any child class.
- The only way to use it is by **creating its own object**.

> A **final class** locks itself — no one can inherit or modify it.