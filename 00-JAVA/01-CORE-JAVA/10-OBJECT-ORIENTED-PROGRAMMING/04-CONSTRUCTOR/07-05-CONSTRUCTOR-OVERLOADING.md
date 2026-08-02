# Constructor Overloading
>  The process of creating multiple constructors with same name in same class but different number of parameters is called **Constructor Overloading**.



![Constructor Overloading](constructorOverloading.png)

#### Example:
```java
class Student {
    int roll;
    String name;
    double percentage;

    // 1️⃣ Default constructor
    Student() {
        System.out.println("Default constructor called");
        roll = 0;
        name = "Unknown";
        percentage = 0.0;
    }

    // 2️⃣ Parameterized constructor (2 parameters)
    Student(int r, String n) {
        System.out.println("Constructor with 2 parameters called");
        roll = r;
        name = n;
        percentage = 0.0;
    }

    // 3️⃣ Parameterized constructor (3 parameters)
    Student(int r, String n, double p) {
        System.out.println("Constructor with 3 parameters called");
        roll = r;
        name = n;
        percentage = p;
    }

    void display() {
        System.out.println("Roll: " + roll);
        System.out.println("Name: " + name);
        System.out.println("Percentage: " + percentage);
        System.out.println("-------------------");
    }
}
```

```java
public class Demo {
    public static void main(String[] args) {
        Student s1 = new Student();                       // calls default
        Student s2 = new Student(101, "Ajay");          // calls 2-param
        Student s3 = new Student(102, "Rahul", 88.5);      // calls 3-param

        s1.display();
        s2.display();
        s3.display();
    }
}
```

```output
Default constructor called
Constructor with 2 parameters called
Constructor with 3 parameters called

Roll: 0
Name: Unknown
Percentage: 0.0
-------------------
Roll: 101
Name: Ajay
Percentage: 0.0
-------------------
Roll: 102
Name: Rahul
Percentage: 88.5
-------------------
```

#### Explanation:
In the above program, the class has **three constructors** — all with the **same name** (`Student`) because every constructor name is same as the class name.  
But the **difference lies in the parameters** — one has no parameters, one has two, and one has three.
So, when we create an object,  
the **compiler checks the arguments** we are passing and then **decides which constructor to call**.

That’s why:
```java
new Student();              // calls default constructor  
new Student(101, "Ajay"); // calls 2-parameter constructor  
new Student(102, "Rahul", 88.5); // calls 3-parameter constructor  
```
This way, we can create objects in **different ways** —  
some with default values, some with partial data, and some with full data.  
That’s the main use of **constructor overloading** —  
it gives **flexibility** in how we initialize our objects.