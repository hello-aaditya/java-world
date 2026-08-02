# Subtask 1: Define a Class with a Parameterized Constructor

**Problem Statement:**

Create a class named `Student` with a parameterized constructor to initialize the student's details such as name, roll number, and course.

**Detailed Instructions:**

1. Create the Student class:
   - Declare three instance variables: `studentName` (String), `rollNumber` (int), and `course` (String).
   - These variables will store the student's name, roll number, and course.

2. Define a parameterized constructor:
   - Create a constructor with three parameters: `String name`, `int rollNo`, and `String courseName`.
   - Inside the constructor, assign the parameter values to the instance variables (`studentName`, `rollNumber`, `course`).

3. Create a method `displayDetails()`:
   - This method should print out the details of the student in a formatted manner.

# Subtask 2: Create Objects Using the Parameterized Constructor and Display Details

**Problem Statement:**

Create multiple Student objects using the parameterized constructor and display their details.

**Detailed Instructions:**

1. In the `main()` method of the Main class:
   - Create three Student objects using the parameterized constructor.
   - Use the following values for each student:
     - Student 1: Name = "Alice Brown", Roll Number = 201, Course = "Mathematics"
     - Student 2: Name = "Bob Green", Roll Number = 202, Course = "Physics"
     - Student 3: Name = "Charlie Black", Roll Number = 203, Course = "Chemistry"

2. Call the `displayDetails()` method for each object:
   - This will display the details of each student, allowing you to verify that the objects were initialized correctly.
## Solution:
```java
class Student {
    String studentName;
    int rollNumber;
    String course;
    
    public Student(String name, int rollNo, String courseName) {
        studentName = name;
        rollNumber = rollNo;
        course = courseName;
    }
    
    public void displayDetails() {
        System.out.println("Student Name: " + studentName);
        System.out.println("Roll Number: " + rollNumber);
        System.out.println("Course: " + course);
    }
}

public class Main {
    public static void main(String[] args) {
        Student student1 = new Student("Alice Brown", 201, "Mathematics");
        Student student2 = new Student("Bob Green", 202, "Physics");
        Student student3 = new Student("Charlie Black", 203, "Chemistry");
        
        student1.displayDetails();
        student2.displayDetails();
        student3.displayDetails();
    }
}
```