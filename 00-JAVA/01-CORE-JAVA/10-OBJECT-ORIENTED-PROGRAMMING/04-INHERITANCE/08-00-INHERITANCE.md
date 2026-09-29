# Let's Imagine a Situation
Suppose a company has built different kinds of robots:
- `TeacherRobot`
- `DoctorRobot`
- `CleanerRobot`

All these three robots share some **common behaviors**:
1. **getCharged()** → They work only when charged.
2. **speak()** → They are able to speak.

These two are **common behaviors** for all robots.

But apart from these, every robot also has its own **individual behaviors**
For Example-

1. Teacher Robot-
	1. **teach()** → Can teach students.
	2. **giveHomework()** → 1. Gives homework.
2. Doctor Robot-
	1. **surgery()** → Performs surgery.
	2. **giveMedicine()** → Suggests or prescribes medicine.
3. Cleaner Robot-
	1. **findDuct()** → Finds dust around.
	2. **clean()** → Cleans the place.
![Inheritance](inheritance.drawio.svg)
## Observation
After looking thoroughly, we can see that:
- Every robot has **some common behaviors** (`getCharged()`, `speak()`),
- And also **some unique behaviors** that belong only to that specific robot.

Now if we try to implement this logic in classes, it may look something like this
#### 1. Teacher Robot
```java
public class TeacherRobot {
	// common behavior
	void getCharged() {
		System.out.println("Robot is getting charged");
	}
	
	void speak() {
		System.out.println("Robot is speaking");
	}
	
	// uncommon behavior
	void teach() {
		System.out.println("Is Teaching");
	}
	
	void giveHomework() {
		System.out.println("Is giving homework");
	}
}
```

#### 2. Doctor Robot
```java
public class DoctorRobot {
	// common behavior
	void getCharged() {
		System.out.println("Robot is getting charged");
	}
	
	void speak() {
		System.out.println("Robot is speaking");
	}
	
	// uncommon behavior
	void surgery() {
		System.out.println("Performing a surgery");
	}
	
	void giveMedicine() {
		System.out.println("Prescribing medicines");
	}
}
```

#### 3. Cleaner Robot
```java
public class CleanerRobot {
	// common behavior
	void getCharged() {
		System.out.println("Robot is getting charged");
	}
	
	void speak() {
		System.out.println("Robot is speaking");
	}
	
	// uncommon behavior
	void findDust() {
		System.out.println("Scanning for duct");
	}
	
	void clean() {
		System.out.println("Time to make everything sparkle and clean!");
	}
}
```

### What We Notice
If you look carefully —  
the size of the code has **grown unnecessarily large**,  
because we have **repeated the same methods** (`getCharged()` and `speak()`) in all three classes.

This is not efficient.

Imagine if there are **50 types of robots** — you’d end up writing the same functions (**`getCharged()`** and **`speak()`**) 50 times!

---
## The Problem

- There’s **code duplication** — the same methods exist in every class.
- If we ever need to update a common method (for example, change how a robot charges),  
    we’d have to update it **in every class manually**.
- It’s hard to maintain and not an ideal approach for reusability.

So here comes the question

> **Is there a way to reduce this code duplication by separating the common behaviors from each class?**

And that’s where the concept of **Inheritance** comes into the picture.

---
# INHERITANCE
> **Inheritance** is the process of **acquiring the properties and behaviors** (data members and methods) of one class into another class.

## Understanding Relationships in Inheritance
From the above example, we can clearly say that —
- `Robot` is the **Parent Class**.
- `TeacherRobot`, `DoctorRobot`, and `CleanerRobot` are the **Child Classes**.
### Note:
- A **Parent Class** is also known as → **Super Class** or **Base Class**.
- A **Child Class** is also known as → **Sub Class** or **Derived Class**.
---
## Relationships in Inheritance
Inheritance in Java mainly defines **two types of relationships**-
1. **IS-A Relationship** [Is-A Relationship](08-02-INHERITANCE-IS-A-RELATIONSHIP.md)
2. **HAS-A Relationship**
---
## Types of Inheritance
1. [Single Inheritance](08-03-SINGLE-LEVEL-INHERITANCE.md)
2. [Multi-Level Inheritance](08-04-MULTI_LEVEL-INHERITANCE.md)
3. [Hierarchical Inheritance](08-05-HIERARCHICAL-INHERITANCE.md)
4. [Hybrid Inheritance](08-06-HYBRID-INHERITANCE.md)
5. [Multiple Inheritance](08-07_MULTIPLE_INHERITANCE.md)
