# Types of Methods during Inheritance
In Java Inheritance, there are three main types of methods-
1. Inherited Methods
2. Overridden Methods
3. Specialized Methods (Child-Specific Methods)
## 1. Inherited Methods
> If a method is **already written in the parent class** and the **child class does not rewrite or modify it**,  
then that method is **automatically available** to the child class because of inheritance.
>
Such a method is called an **Inherited Method**.
#### Parent Class
```java
class Parent {
	void display() {
		System.out.println("Inside Parent method");
	}
}
```
#### Child Class
```java
class Child extends Parent {
	/*
		display() method automatically inherited from Parent class
		because Child is inherited from the Parent class.
		display() method is not visible in Child class,
		but we can still call it using the child object.
	*/
}
```
#### Main Class
```java
class Main {
	public static void main(String[] args) {
		Child c = new Child();
		c.display(); // calling inherited method
	}
}
```
#### Output
```markdown
Inside Parent method
```
## 2. Overridden Methods
> If a method is **already present in the parent class**,  
and the **child class writes the same method again** with the **same name, same parameters, and same return type**,  
then the child’s version **replaces** the parent’s version while calling it through the child object.
>
Such a method is called an **Overridden Method**.
#### Parent Class
```java
class Parent {
	void display() {
		System.out.println("Inside Parent method");
	}
}
```
#### Child Class
```java
class Child extends Parent {
	// Overriding the parent method
	void display() {
		System.out.println("Inside Child method");
	}
}
```
#### Main Class
```java
class Main {
	public static void main(String[] args) {
		Child c = new Child();
		c.display(); // calls Child version
	}
}
```
#### Output
```markdown
Inside Child method
```
### @Override Annotation
- `@Override` is an **annotation** used above a method that **overrides** a parent class method.
- It is **not mandatory**, but **highly recommended**.
- If you make a mistake in the method signature (like wrong name or parameters),  
	the compiler will show an **error**, helping you catch issues early.
- It makes our code **easier to read and understand**.
#### Example (if we make a mistake without @Override)
#### Parent Class
```java
class Parent {
	void display() {
		System.out.println("Inside Parent method");
	}
}
```
#### Child Class
```java
class Child extends Parent {
	// typo in method name (no @Override check)
	void disply() {
		System.out.println("Inside Child method");
	}
}
```
This code will **not override** the parent’s method — it will simply create a **new method** in the Child class because of the spelling mistake.  
If you had used `@Override`, the compiler would immediately show an **error**.
### Example 1 — Correct use of `@Override`
#### Parent Class
```java
class Parent {
	void display() {
		System.out.println("Inside Parent display method");
	}

	void show() {
		System.out.println("Inside Parent show method");
	}
}
```
#### Child Class
```java
class Child extends Parent {
	@Override
	void display() {   // Correctly overriding parent method
		System.out.println("Inside Child display method");
	}

	@Override
	void show() {      // Correctly overriding parent method
		System.out.println("Inside Child show method");
	}
}
```
#### Main Class
```java
public class Main {
	public static void main(String[] args) {
		Child c = new Child();
		c.display();
		c.show();
	}
}
```
#### Output
```markdown
Inside Child display method
Inside Child show method
```
## 3. Specialized Methods (Child-Specific Methods)
> If a method is **written only inside the child class** and **does not exist in the parent class**,  
then that method is called a **Specialized Method**.
#### Parent Class
```java
class Parent {
	void display() {
		System.out.println("Inside Parent method");
	}
}
```
#### Child Class
```java
class Child extends Parent {

	void display() {     // specialized method
		System.out.println("Inside Specialized method");
	}
}
```
#### Main Class
```java
class Main {
	public static void main(String[] args) {
		Child c = new Child();
		
		c.display();     // specialized method
	}
}
```
#### Output
```markdown
Inside Specialized method
```

---
### All Three Methods in One Program
#### Parent Class
```java
class Parent {
	// Inherited Method
	void inheritedMethod() {
		System.out.println("This is an Inherited Method");
	}
	
	// Overridden Method (Parent version)
	void overriddenMethod() {
		System.out.println("This is Parent version of Overridden Method");
	}
}
```
#### Child Class
```java
class Child extends Parent {
	// Overridden Method (Child version)
	@Override
	void overriddenMethod() {
		System.out.println("This is Child version of Overridden Method");
	}
	
	// Specialized Method
	void specializedMethod() {
		System.out.println("This is a Specialized Method");
	}
}
```
#### Main Class
```java
public class Main {
	public static void main(String[] args) {
		Child c = new Child();  // creating object of child class
		
		c.inheritedMethod();     // inherited method
		c.overriddenMethod();    // overridden method
		c.specializedMethod();   // specialized method
	}
}
```
#### Output
```markdown
This is an Inherited Method
This is Child version of Overridden Method
This is a Specialized Method
```