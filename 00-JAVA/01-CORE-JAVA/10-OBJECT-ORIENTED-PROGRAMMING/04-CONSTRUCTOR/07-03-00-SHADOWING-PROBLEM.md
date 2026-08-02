```java
class Student {
    int roll;
    String name;
    double percentage;

    Student(int a, String b, double c) {
        roll = a;
        name = b;
        percentage = c;
    }
}
```
Here, we are assigning values using different variable names (`a`, `b`, `c`).  
This works fine — but **it’s not a good coding practice**.  
**Why?**  
Because variable names should be **meaningful and consistent**,  and they should clearly represent what they store.

---
So instead of using `a`, `b`, and `c`,  
we write a **better version** like this-
```java
class Student {
    int roll;
    String name;
    double percentage;

    Student(int roll, String name, double percentage) {
        roll = roll;
        name = name;
        percentage = percentage;
    }
}
class Main {
	public static void main(String[] args) {
		Student s1 = new Student(101, "Ajay", 85.5);
		System.out.println("Roll: " + s1.roll);
		System.out.println("Name: " + s1.name);
		System.out.println("Percentage: "+ s1.percentage);
	}
}
```
Looks cleaner, right?  
But there’s a **problem here** — and this leads us to an important topic called the **Shadowing Problem**.


At first glance, this looks fine —  
it seems like we are assigning values to `roll`, `name`, and `percentage`.  
But when we run this program and later try to print those values,  
we get something like-
```output
Roll: 0
Name: null
Percentage: 0.0
```
Wait… what just happened?  
Didn’t we pass values through the constructor?  
Then why are all values still at their **default state**?

Let’s understand this carefully.

---

## Step-by-Step Flow (Story)

1. The JVM starts execution from the `main()` method.  
    The **static segment** is created in memory, and the control enters activation record of the `main()`.
    
2. When we create an object:
	```java
	Student s1 = new Student(101, "Ajay", 85.5);
	```
	The control goes to the **constructor** of the `Student` class that has **three parameters**.
3. Inside that constructor:
	```java
	Student(int roll, String name, double percentage);
	```
	- The values `101`, `"Aaditya"`, and `85.5` are **copied into local variables**  
	    → these are **constructor parameters**.
    
	- So now:
	  ```java
		roll = 101
		name = "Ajay"
		percentage = 85.5

	  ```
4.  Next, the control executes:
	```java
	roll = roll;
	name = name;
	percentage = percentage;
	```
	But here’s the twist ⚠️  
	Both **instance variables** and **local variables** have the same names.
	
	In Java, **local variables always get priority** over instance variables when the names are identical.  
	This means:

	- The `roll` on the left and the `roll` on the right both refer to the **local variable**.
	- So we are **assigning a variable to itself** — `roll (local) = roll (local)`.
	- The instance variable is never touched.
5.  As a result, all **instance variables remain uninitialized**,  
	so they hold **default values**:
	```java
	roll = 0
	name = null
	percentage = 0.0
	```
	![Shadowing Problem](shadowingProblem.png)
---
## The Root Cause

This issue is known as the **Shadowing Problem**.

> When a local variable (like a parameter) has the **same name** as an instance variable,  
> it **shadows** or hides the instance variable inside that block of code.

So the local variable wins, and the instance variable becomes unreachable in that scope.

---
## How to Fix It — Using `this` Keyword
To clearly tell Java that we are talking about the **instance variables**,  
we use the **`this` keyword**.
```java
class Student {
    int roll;
    String name;
    double percentage;

    Student(int roll, String name, double percentage) {
        this.roll = roll;
        this.name = name;
        this.percentage = percentage;
    }
}
```
Now the meaning changes to:
- `this.roll` → instance variable
- `roll` → local parameter  
    So, values are properly assigned.
---
## Behind the Scene (What Happens Internally)
When we write:
```java
this.roll = roll;
```
The `this` keyword points to the **current object** being created in heap.  
So,
- `this.roll` → the `roll` variable of that current object.
- `roll` → the local parameter passed from the constructor.

Now the assignment becomes:
```java
(instance variable) = (local variable)
```
which correctly initializes the object’s data.

---
## Output After Fix
```java
Student s1 = new Student(101, "Ajay", 85.5);
System.out.println(s1.roll);
System.out.println(s1.name);
System.out.println(s1.percentage);
```
**Output:**
```output
101
Ajay
85.5
```
