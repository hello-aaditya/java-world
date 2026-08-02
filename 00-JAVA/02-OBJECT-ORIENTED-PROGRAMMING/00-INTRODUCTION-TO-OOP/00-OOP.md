# What is Object Oriented Programming (OOP)?
Object-Oriented Programming is a way of writing programs where instead of just writing **functions and logic**, we organize everything around objects that represent real-life entities.
> "The two core building blocks of OOP are: **Class** and **Object**."
## What is a Class?
In Java, A Class is a **blueprint** / **template** for creating objects. 
or we can say- Class is definition of objects.

It represents:
- **State** using variables
- **Behavior** using methods.
#### Example: University Student class
##### Class Design

| Category                      | Members                                                |
| ----------------------------- | ------------------------------------------------------ |
| Has (Properties / Attributes) | `rollNo` (int), `name` (String), `department` (String) |
| Does (Behaviors / Methods)    | `study()`, `play()`, `exam()`                          |

```JAVA
class Student {

	// Has (Properties)
	int rollNo;
	String name;
	String department;
	
	// Does (Behaviors)
	void study() {
		System.out.println("Studying");
	}
	void play() {
		System.out.println("Playing");
	}
	void exam() {
		System.out.println("Appearing in the examination");
	}
}
```
## What is an Object?
An Object is an instance of a class that represents a real-world entity with **Properties (Variables)** and **Behaviors (Methods)**.
- An Object can be created by using `new` keyword.
**Each object has:**
- **Properties (variables)** → what it _has_
- **Behaviors (Methods)** → what it _does_
##### Example in Real Life:
##### If i consider an example of a `car` then-
- Car **Has** → color, brand, speed   
- Car **Does** → start, stop, accelerate

In OOP, `Car` is the **class** (blueprint), and Toyota, BMW, Tesla are individual **objects** created from that class — each with their own values.

##### If i consider an example of a `student` then-
- What a student **Has** → rollNo, name, department
- What does an Student Do → study, play, exam
### How to create an Object in Java
```JAVA
public class Main {
	public static void main(String[] args) {
		// creating first student object
		Student s1 = new Student();
		s1.rollNo = 60301;
		s1.name = "Ajay";
		s1.department = "Computer Science";
		
		// printing student details
		System.out.println(s1.rollNo);
		System.out.println(s1.name);
		System.out.println(s1.department);
		
		
		// call methods
		s1.study();
		s1.play();
		s1.exam();
	}
}
```
#### Explanation:
- `Student s1 = new Student();` → **Creates an object** named `s1`.
- `s1.name = "Ajay";` → Assigns the value "Ajay" to the name property of object s1.
- `s1.study();` → Calls the **method** to showcase its behavior.
**[Types of Objects](30-NORMAL-ANONYMOUS-GARBAGE-OBJECTS.md)**

[**PTO**](10-OOP-AND-MEMORY-MANAGEMENT.md)