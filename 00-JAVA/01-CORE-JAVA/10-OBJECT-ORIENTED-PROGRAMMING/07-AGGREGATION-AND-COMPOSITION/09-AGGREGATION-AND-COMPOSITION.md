# Aggregation & Composition
## HAS-A Relationship
We know that:
- **IS-A Relationship** → represents **inheritance** (like _Dog is an Animal_).
- **HAS-A Relationship** → represents **association** (like _Car has an Engine_).

So, a **HAS-A relationship** means **one class contains or uses another class** as part of its functionality.
> When one class **has** an object of another class, we say that there is a **HAS-A relationship** between them.
>
> A **HAS-A Relationship** is a type of **association** in OOP where:
	 → One class **includes another class** as a **data member** (object reference). 
	 → It shows that one object **uses**, **owns**, or **contains** another object.

##### For example:
```java
class Mobile {
    OS o = new OS();  // Mobile has an OS
}
```
Here, the `Mobile` class **has** an object of class `OS`.  
So we say **Mobile HAS-A OS**.  
This means `Mobile` **depends on** `OS` for its operation.
## Purpose of HAS-A Relationship
Why do we use HAS-A relationship?
1. **Code Reusability:**  
    Instead of rewriting code in every class, we can reuse functionalities by creating objects of other classes.
    
2. **Modularity:**  
    Each class focuses on one task. This makes our program organized and easy to maintain.
    
3. **Real-world modeling:**  
    Most real-life objects have parts or components —  
    A _Car has an Engine_, a _Mobile has a Battery_, etc.  
    HAS-A relationship helps us represent such real-world structures in programming.
## Types of HAS-A Relationship
There are **two main types** of HAS-A relationships in Java:
1. **Aggregation** → _Weak bonding_
2. **Composition** → _Strong bonding_
![Aggragation & Composition](hasARelationaship.drawio.svg)
### 1. Aggregation
("Friends with benefits" of Object Relationships 😄)

##### Definition
**Aggregation** is a **weaker form of association** where one class **uses** another class, but both can **exist independently**.

> It represents a _"has-a"_ relationship where objects are **loosely connected**.

In simple words —  
if one object is destroyed, the other can still exist.

| Characteristic   | Explanation                                                              |
| ---------------- | ------------------------------------------------------------------------ |
| **Dependency**   | Weak dependency. The main object can exist without the contained object. |
| **Lifespan**     | Both objects have **independent lifecycles**.                            |
| **Coupling**     | Loose coupling — less dependent, more flexible.                          |
| **UML Notation** | Represented using a **hollow diamond (◊)** in UML.                       |
| **Ownership**    | Shared ownership — multiple objects can share one contained object.      |

Example:
##### OS.java
```java
package inheritanceHasA;

public class OS {
	OS() {
		System.out.println("OS is installed");;
	}
	
	void checkOS() {
		System.out.println("OS is still executing");
	}
}
```
##### Mobile.java
```java
package inheritanceHasA;

public class Mobile {
	OS o = new OS();
	
	Mobile() {
		System.out.println("Mobile created with OS");
	}
	
	void hasA(Charger c) {
		System.out.println("Mobile is using " + c.name + " charger");
	}
}
```
##### Charger.java
```java
package inheritanceHasA;

public class Charger {
	String name;
	
	Charger(String s) {
		name = s;
		System.out.println("Charger Created: " + name);
	}
	
	void getCharger() {
		System.out.println("Charger can be used for charging");
	}
}
```
##### Main.java
```java
package inheritanceHasA;

public class Main {

	public static void main(String[] args) {
		Mobile m = new Mobile();
		
		Charger c = new Charger("HP");
		m.hasA(c);
		m.o.checkOS();
		c.getCharger();
	}

}
```

##### Output
```markdown
OS is installed
Mobile created with OS
Charger Created: HP
Mobile is using HP charger
OS is still executing
Charger can be used for charging
```
When we run the program, the JVM’s control enters the `main()` method.  
The first line inside `main()` is:
```java
Mobile m = new Mobile();
```
So as part of initialization, a new `OS` object is also created in the heap.  
The `OS()` constructor runs first and prints:
```markdown
OS is installed
```
Then control comes back to `Mobile()` constructor, and it prints:
```markdown
Mobile created with OS
```
At this point, the `Mobile` object has an `OS` — this is **composition**, because the OS is created and owned by the Mobile itself.

Now, back in the main method, we have:
```java
Charger c = new Charger("HP");
```
This line creates another independent object in the heap, a `Charger` object, and prints:
```markdown
Charger Created: HP
```
This `Charger` object is created separately and does not belong to the Mobile object by default.

Then we do:
```java
m.hasA(c);
```
Assuming that in our `Mobile` class we have a method like this:
```java
void hasA(Charger c) {
    System.out.println("Mobile is using " + c.name + " charger");
}
```
![Aggregation](AggregationCompositionMemoryBlock.drawio.svg)
When this method is called, we are **passing the reference** of the `Charger` object into the `Mobile` object.  
But notice — we’re _not creating a new charger inside the Mobile class_.  
We’re simply _using_ an already existing `Charger` object that was created separately in the heap.

So the `Mobile` and `Charger` objects now **exist independently** in memory.  
Even if the `Mobile` object is destroyed or set to null, the `Charger` object will still remain in memory until the garbage collector clears it.

That’s exactly what makes this **aggregation**.
### 2. Composition
("Till death do us part" of Object Relationships ❤️)

##### Definition
**Composition** is a **strong form of association** where one class **owns** another class completely.  
The contained object’s **lifecycle depends** on the container object.

> If the main object is destroyed, the contained object also gets destroyed.

In simple words —  
If one dies, the other dies too. 😄

|Characteristic|Explanation|
|---|---|
|**Dependency**|Strong dependency. The contained object cannot exist independently.|
|**Lifespan**|Both objects share the same lifecycle.|
|**Coupling**|Tight coupling — one object fully owns the other.|
|**UML Notation**|Represented using a **filled diamond (◆)** in UML.|
|**Ownership**|Exclusive ownership — the contained object belongs only to one container.|
#### Example
##### OS.java
```java
class OS {
    OS() {
        System.out.println("OS is installed");
    }

    void checkOS() {
        System.out.println("OS is still executing");
    }
}
```
##### Mobile.java
```java
class Mobile {
    OS o = new OS();  // Composition (object created inside the class)

    Mobile() {
        System.out.println("Mobile created with OS");
    }
}
```
##### Main.java
```java
public class Main {
    public static void main(String[] args) {
        Mobile m = new Mobile();
    }
}
```
##### Output
```markdown
OS is installed
Mobile created with OS
```

When we run the program, the **control of JVM first enters the Main class**, and the very first method that gets executed is the `main()` method. Inside the main method, the line
```java
Mobile m = new Mobile();
```
is encountered.
The control finds the `new` keyword. Now, the moment JVM sees the `new` keyword, it knows that a **new object** needs to be created in the **heap memory**.  
So it first **allocates a block of memory** for the `Mobile` object — let’s say at address `0x1000`.

Now, before the `Mobile()` constructor body actually starts executing,  
the JVM first initializes **all the instance variables** of that class.  
This is an important point — **instance variables are always initialized before the constructor body runs.**

Inside the `Mobile` class, we have:
```java
OS o = new OS();
```
So now, JVM encounters `new OS()`. Again, it allocates another separate block of memory inside the heap (say address `0x2000`) for this OS object. The OS object is **not created inside the Mobile’s heap block** — both are separate objects in the heap.
The Mobile object simply stores the **address (reference)** of the OS object in its variable `o`.
![](compositionMemoryBlock.drawio.svg)
Once the OS object is created, the control enters the `OS()` constructor, which prints:
```markdown
OS is installed
```
After the OS constructor finishes, the control goes back to the Mobile class to finish its own constructor. Now the `Mobile()` constructor runs, and it prints:
```markdown
Mobile created with OS
```

At this point, both objects are fully ready in memory: the `Mobile` object is at `0x1000`, and it holds a reference to the `OS` object at `0x2000`. So, visually, the Mobile object has a variable `o` that points to another object — the OS.

The console output becomes:
```markdown
OS is installed
Mobile created with OS
```

This whole process clearly represents **composition**, because the OS object is completely dependent on the Mobile object. Every time a Mobile is created, a new OS is automatically created along with it. And when the Mobile object gets destroyed, its OS also becomes unreachable and will be collected by the Garbage Collector. So, in simple words — a Mobile **has-an** OS, and their lifecycles are tightly bound. That’s why composition is also called a **strong HAS-A relationship**. 

---
```java
package inheritanceHasA;

public class Main {

	public static void main(String[] args) {
		Mobile m = new Mobile();
		m.o.checkOs();
		m = null;
		m.o.checkOs();
	}

}
```
![](compositionMemoryBlockNull.drawio.svg)

##### Output
```markdown
OS is installed
Mobile created with OS
OS is still executing
Exception in thread "main" java.lang.NullPointerException:
Cannot read field "o" because "m" is null
```
##### Explanation
When we assign `m = null`, we don’t delete the object — Java never deletes objects manually.  
We only remove the **reference variable** that was pointing to that object.  
Now, there’s no direct way to reach the Mobile object in the heap from the stack.

Because of that, when we try to do `m.o.checkOs()`, JVM says:

> “Wait, `m` itself is null. You’re trying to access something through nothing.”

That’s why it throws a `NullPointerException`.

Also note — at this point, both the Mobile and OS objects in the heap are **still in memory**, but since there’s **no reference** pointing to them, they are now **eligible for Garbage Collection**.

Eventually, JVM’s Garbage Collector will remove them to free heap space.

---
