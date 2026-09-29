# Types of Polymorphism
In Java, polymorphism is mainly of two types:
1. **Runtime Polymorphism (Dynamic Polymorphism)**
2. **Compile-Time Polymorphism (Static Polymorphism)**
## 1. Runtime Polymorphism
>Runtime polymorphism happens **during execution (runtime)**.
>It works when:
>- Child classes **override** the parent class methods
>- We **pass child objects** to a method that accepts **parent type reference**    
>- The actual object is created inside **heap memory at runtime**, and the overridden method of that object is executed    
>
>This is called **runtime polymorphism** because the decision of “which method to run” happens **at running time**.

### Example of Runtime Polymorphism
#### Parent.java
```java
public class Parent {
    void display1() {
        System.out.println("Inside Parent-display1 Method");
    }
    void display2() {
        System.out.println("Inside Parent-display2 Method");
    }
}
```
#### Child1.java
```java
public class Child1 extends Parent {
    
    @Override
    void display2() {
        System.out.println("Inside the Child1-display2 Overridden Method");
    }
    
    // Specialized Method
    void display3() {
        System.out.println("Inside the Child1-display3 Specialized Method");
    }
}
```
#### Child2.java
```java
public class Child2 extends Parent {
    
    @Override
    void display2() {
        System.out.println("Inside the Child2-display2 Overridden Method");
    }
    
    // Specialized Method
    void display3() {
        System.out.println("Inside the Child2-display3 Specialized Method");
    }
}
```
#### Main.java
```java
public class Main1 {

    public static void main(String[] args) {

        Child1 c1 = new Child1();
        accessMethod(c1);   // Parent reference → Child1 object

        Child2 c2 = new Child2();
        accessMethod(c2);   // Parent reference → Child2 object
    }

    public static void accessMethod(Parent ref) {
        ref.display1();   // inherited method
        ref.display2();   // overridden method
        System.out.println("_______________________");
    }
}
```
#### Output
```markdown
Inside Parent-display1 Method
Inside the Child1-display2 Overridden Method
Inside the Child1-display3 Specialized Method
_______________________
Inside Parent-display1 Method
Inside the Child2-display2 Overridden Method
Inside the Child2-display3 Specialized Method
_______________________
```
![Upcasting](upcasting.svg)
#### Explanation
- `accessMethod(Parent1 ref)` accepts **parent type reference**
- We pass **child objects**: `c1` and `c2`
- Upcasting happens automatically → child object stored in parent reference
- `ref.display2()` runs the overridden method of **the actual child object**
So:
- When Child1 is passed → Child1 version runs
- When Child2 is passed → Child2 version runs

**One method → many forms of output**  
That is the meaning of **polymorphism**.

---
## 2.  Compile-Time Polymorphism
> In compile-time polymorphism, one class contains **multiple methods with the same name**, but:
>- different number of parameters
>- or different types of parameters
>- or different order of parameters
>
>Here also we have **one method name** and **many forms** → so it is polymorphism.  
But the method to call is decided at **compile time**, not runtime.
>
>This is called **Method Overloading**.

### Example of Compile-Time Polymorphism
#### Calculator.java
```java
package polymorphism.compiletimePolymorphism;

public class Calculator {
	
	// Method-1: add two integers
	int add(int number1, int number2) {
		return number1+number2;
	}
	
	// Method-2: add three integers
	int add(int number1, int number2, int number3) {
		return number1+number2+number3;
	}
	
	// Method-3: add two double values
	double add(double number1, double number2) {
		return number1+number2;
	}
}
```
#### CalculatorMain.java
```java
package polymorphism.compiletimePolymorphism;

public class CalculatorMain {

	public static void main(String[] args) {
		
		Calculator calc = new Calculator();
		
		System.out.println("Two integer values addition: " + calc.add(10, 20));
		System.out.println("Three integer values addition: " + calc.add(10, 15, 25));
		System.out.println("Two double values addition: " + calc.add(40.0, 60.0));
	}

}
```
#### Output
```markdown
Two integer values addition: 30
Three integer values addition: 50
Two double values addition: 100.0
```
#### Explanation
- All three methods have **the same name** (`add`), But each has a **different parameter list**
- So the compiler treats them as **multiple forms** of the same method name
- That is the **1:Many**.

---
---
![](polymorphismSummarization.drawio.svg)
