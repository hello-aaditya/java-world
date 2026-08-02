## Example Showing Error When Accessing `display3()` Without `instanceof`
#### Parent1.java
```java
package polymorphism.runtimePolymorphism;

public class Parent1 {
    void display1() {
        System.out.println("Inside Parent1-display1 Method");
    }

    void display2() {
        System.out.println("Inside Parent1-display2 Method");
    }
}
```
#### Child1.java
```java
package polymorphism.runtimePolymorphism;

public class Child1 extends Parent1 {

    @Override
    void display2() {
        System.out.println("Inside the Child1-display2 Overridden Method");
    }

    void display3() {
        System.out.println("Inside the Child1-display3 Specialized Method");
    }
}
```
#### Child2.java
```java
package polymorphism.runtimePolymorphism;

public class Child2 extends Parent1 {

    @Override
    void display2() {
        System.out.println("Inside the Child2-display2 Overridden Method");
    }

    void display3() {
        System.out.println("Inside the Child2-display3 Specialized Method");
    }
}
```
#### Main.java — Wrong Downcasting Example
```java
package polymorphism.runtimePolymorphism;

public class Main1 {

    public static void main(String[] args) {

        // Parent reference holding Child2 object
        Parent1 ref = new Child2();
        ref.display1();
        ref.display2();

        // Trying to downcast to Child1 (WRONG)
        // This will compile but fail at runtime
        ((Child1)ref).display3();   // ❌ ClassCastException
    }
}
```
#### Output (Runtime Error Outpu)
```markdown
Inside Parent1-display1 Method
Inside the Child2-display2 Overridden Method
Exception in thread "main" java.lang.ClassCastException:
polymorphism.runtimePolymorphism.Child2
cannot be cast to
polymorphism.runtimePolymorphism.Child1
```
### Explanation
We have:
- **Parent1** → parent class
- **Child1** and **Child2** → two child classes
- Both children override `display2()`
- Both children have their own specialized method `display3()`
Everything is fine until we try to **downcast** incorrectly.

##### Main.java — Wrong Downcasting
```java
Parent1 ref = new Child2();  // Parent reference holding Child2 object

((Child1)ref).display3();    // ❌ Wrong downcast
```
##### 1. What happens at this line?
```java
Parent1 ref = new Child2();
```
- A **Child2 object** is created inside heap memory.
- The reference `ref` is of type **Parent1**, but points to a **Child2** object.

Memory picture:
```markdown
ref -----------------> Child2 object
```
This is **upcasting**, and it is valid.

##### 2. What we try to do next
```java
((Child1)ref).display3();
```
Here we are telling Java:
> “Take this `ref` and treat it as a **Child1** object.”

But the **actual object** inside heap is **Child2**, not Child1.

##### 3. Why does Java throw an error?
Child1 and Child2 are **siblings**:
```markdown
Parent1
   |____ Child1
   |____ Child2
```
Sibling classes **can never be cast into each other**.
**Only valid:**
- Parent1 → Child1 (downcast if it is actually Child1)
- Parent1 → Child2 (downcast if it is actually Child2)

**Invalid:**
- Child2 → Child1
- Child1 → Child2

Because there is **no parent-child relationship** between them.

### What is the correct way to call `display3()` from a parent reference that actually points to a child object?
or 
### If `((Child1)ref).display3()` causes an error when `ref` holds a Child2 object, then what is the safe technique to call `display3()`?
## Solution: `instanceof` + Downcasting
```java
if(ref instanceof Child1) {
    ((Child1)ref).display3();
}
```
Or:
```java
if(ref instanceof Child2) {
    ((Child2)ref).display3();
}
```
# Use of `instanceof`
#### Main.java
```java
package polymorphism.runtimePolymorphism;

public class Main1 {

	public static void main(String[] args) {
		
		Child1 c1 = new Child1();
		accessMethod(c1);
		
		Child2 c2 = new Child2();
		accessMethod(c2);
	}
	
	public static void accessMethod(Parent1 ref) {
		ref.display1();
		ref.display2();
		
		if(ref instanceof Child1) {
			((Child1)(ref)).display3();
		} else {
			((Child2)(ref)).display3();
		}
		System.out.println("_______________________");
	}
}
```
#### Output
```markdown
Inside Parent1-display1 Method
Inside the Child1-display2 Overridden Method
Inside the Child1-display3 Specialized Method
_______________________
Inside Parent1-display1 Method
Inside the Child2-display2 Overridden Method
Inside the Child2-display3 Specialized Method
_______________________
```

### Explanation
- `ref instanceof Child1` → checks if `ref` is holding a Child1 object
- If true → safe to downcast → Child1’s `display3()` runs
- Otherwise → object must be Child2 → downcast to Child2 and run `display3()`

This way, one method (`accessMethod`) can handle **both child objects** safely.