# IS-A Relationship
> “IS-A” relationship can be achieved with the help of **extends** keyword.
![Is-A-Relationship](inheritance-is-a-relationship.drawio.svg)

We can say-
1. `TeacherRobot` **is a** Robot.
2. `DoctorRobot` **is a** Robot.
3. `CleanerRobot` **is a** Robot.
So,
Robot will be the **parent (super) class**, and the other robots will be **child (sub) classes**.

# Example
### Parent Class: `Robot`
```java
// Parent class (Super class / Base class)
public class Robot {
	// common behaviors for all robots
	void getCharged() {
		System.out.println("Robot is getting charged");
	}
	
	void speak() {
		System.out.println("Robot is speaking");
	}
}
```
### Child Class: `TeacherRobot`
```java
// Child classes (Sub class / Derived class)
public class TeacherRobot extends Robot {
	// unique behaviors
	void teach() {
		System.out.println("Is Teaching");
	}
	
	void giveHomework() {
		System.out.println("Is giving homework");
	}
}
```
### Child Class: `DoctorRobot`
```java
// Child classes (Sub class / Derived class)
public class DoctorRobot extends Robot {
	// unique behaviors
	void surgery() {
		System.out.println("Performing a surgery");
	}
	
	void giveMedicine() {
		System.out.println("Prescribing medicines");
	}
}
```
### Child Class: `CleanerRobot`
```java
// Child classes (Sub class / Derived class)
public class CleanerRobot extends Robot {
	// unique behaviors
	void findDust() {
		System.out.println("Scanning for dust");
	}
	
	void clean() {
		System.out.println("Time to make everything sparkle and clean!");
	}
}
```
### **Explanation**
- `TeacherRobot`, `DoctorRobot`, `CleanerRobot` **inherit** common behaviors from `Robot`.
- This shows **IS-A relationship** clearly:
    - TeacherRobot **is a** Robot
    - DoctorRobot **is a** Robot
    - CleanerRobot **is a** Robot
