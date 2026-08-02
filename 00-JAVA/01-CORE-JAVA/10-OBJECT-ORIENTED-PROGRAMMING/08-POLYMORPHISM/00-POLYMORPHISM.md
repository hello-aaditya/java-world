# Upcasting
> Upcasting is the process of creating a child object and assigning it to a parent-type reference.
> In upcasting, the child object is treated at the parent level, but overridden methods still execute from the child class.

```java
Developer dev = new JavaDeveloper();
```
Means,
**Child → Parent reference**

## Basic Upcasting Example
#### Example 1
![](devObject.drawio.svg)
```java
Developer dev = new JavaDeveloper();
dev.work();
dev.project();
```

#### Example 2
![](devObject3.drawio.svg)
```java
Developer dev = new PythonDeveloper();
dev.work();
dev.project();
```

- `dev` (parent reference) sits in **stack**.
- `new JavaDeveloper()` object sits in **heap**.
- Although the reference is of type `Developer`,  
    the **actual object** is **JavaDeveloper**.

So, when we call:
```java
dev.work();
```
Java checks:
1. What object is `dev` pointing to? → **JavaDeveloper** or **PythonDeveloper**
2. Is `work()` overridden there? → Yes
3. Call child version.



---
![Developer](polymorphism.drawio.svg)
##### Developer.java
```java
public class Developer {
    void work() {
        System.out.println("Developer is working");
    }
    void project() {
        System.out.println("Developer is doing project");
    }
}
```
##### JavaDeveloper.java
```java
public class JavaDeveloper extends Developer {
    @Override
    void work() {
        System.out.println("Java Developer is working");
    }
    @Override
    void project() {
        System.out.println("Java Developer is doing project");
    }
}
```
##### PythonDeveloper.java
```java
public class PythonDeveloper extends Developer {
    @Override
    void work() {
        System.out.println("Python Developer is working");
    }
    @Override
    void project() {
        System.out.println("Python Developer is doing project");
    }
}
```
##### Main.java (Without Polymorphism)
```java
public class Main {
    public static void main(String[] args) {

        JavaDeveloper jd = new JavaDeveloper();
        jd.work();
        jd.project();

        PythonDeveloper pd = new PythonDeveloper();
        pd.work();
        pd.project();

        // If there are 10 developers → 20 method calls
    }
}
```
##### Output:
```markdown
Java Developer is working
Java Developer is doing project
Python Developer is working
Python Developer is doing project
```

#### Memory Visual
![](polymorphismMemoryMap.drawio.svg)**Now the question is — if I use a parent type reference (Developer dev), can I still call the child class overridden methods?**  
Because till now, we called `work()` and `project()` using child references (`JavaDeveloper jd`, `PythonDeveloper pd`).  
But what happens if the reference is from the parent class?

##### Developer.java
```java
public class Developer {
    void work() {
        System.out.println("Developer is working");
    }
    void project() {
        System.out.println("Developer is doing project");
    }
}
```
##### JavaDeveloper.java
```java
public class JavaDeveloper extends Developer {
    @Override
    void work() {
        System.out.println("Java Developer is working");
    }
    @Override
    void project() {
        System.out.println("Java Developer is doing project");
    }
}
```
##### PythonDeveloper.java
```java
public class PythonDeveloper extends Developer {
    @Override
    void work() {
        System.out.println("Python Developer is working");
    }
    @Override
    void project() {
        System.out.println("Python Developer is doing project");
    }
}
```
##### Main.java
```java
public class Main {
    public static void main(String[] args) {

        Developer dev;

        dev = new JavaDeveloper();
        dev.work();
        dev.project();

        dev = new PythonDeveloper();
        dev.work();
        dev.project();
    }
}
```
##### Explanation:
1. **`Developer dev;`**
	![](dev.drawio.svg)
	- Only a **reference variable** is created in stack memory.
	- No object is created yet.
	- `dev` can _point to_ any object that is a Developer or its child.
2. **`dev = new JavaDeveloper();`**
	Now in **heap memory**, a `JavaDeveloper` object is created:
	![](devObject.drawio.svg)
	- The `dev` reference now **points to** this JavaDeveloper object.
	- It _automatically uses_ JavaDeveloper’s overridden methods.
	So:
	```java
	dev.work();    // Calls JavaDeveloper's work()
	dev.project(); // Calls JavaDeveloper's project()
	```
3. **`dev = new PythonDeveloper();`**
	Now this line **changes the object** that `dev` points to.
	![](devObject2.drawio.svg)
	- The previous JavaDeveloper object still exists (until GC).
	- `dev` now points to a **new PythonDeveloper** in heap.
	So, 

	```java
	dev.work();    // Calls PythonDeveloper's work()
	dev.project(); // Calls PythonDeveloper's project()
	```

	Same reference → **different behavior**, because  
	actual object changed → methods resolved at runtime.
##### Output:
```markdown
Java Developer is working
Java Developer is doing project
Python Developer is working
Python Developer is doing project
```

> The process of creating a child object and assigning it to a parent-type reference is called as **UPCASTING**.
> In upcasting, the child object is treated at the parent level, but overridden methods still execute from the child class.

---
Till now, we used a parent reference to call child overridden methods.  
But we can still reduce our code further by writing **one common method** that accepts the parent type (`Developer`).  
This method can handle any child object due to **polymorphism**.
#### Developer.java
```java
public class Developer {
    void work() {
        System.out.println("Developer is working");
    }
    void project() {
        System.out.println("Developer is doing project");
    }
}
```
#### JavaDeveloper.java
```java
public class JavaDeveloper extends Developer {
    @Override
    void work() {
        System.out.println("Java Developer is working");
    }
    @Override
    void project() {
        System.out.println("Java Developer is doing project");
    }
}
```
#### PythonDeveloper.java
```java
public class PythonDeveloper extends Developer {
    @Override
    void work() {
        System.out.println("Python Developer is working");
    }
    @Override
    void project() {
        System.out.println("Python Developer is doing project");
    }
}
```
#### Main.java
```java
public class Main {
    public static void main(String[] args) {

        JavaDeveloper jd = new JavaDeveloper();
        accessMethod(jd);     // Passing child object

        PythonDeveloper pd = new PythonDeveloper();
        accessMethod(pd);     // Passing another child object
    }

    public static void accessMethod(Developer dev) {
        dev.work();           // Calls child overridden methods
        dev.project();
    }
}
```
#### Output
```markdown
Java Developer is working
Java Developer is doing project
Python Developer is working
Python Developer is doing project
```
#### Explanation
Here, the method `accessMethod(Developer dev)` takes a **parent type reference**, which means we can pass **any child object** to it.  
Inside the method, the overridden methods of the actual child object are executed.

---
# Polymorphism
Polymorphism means “**many forms**”.
> When a parent-type reference holds different child objects, and the overridden methods of those child objects run based on the actual object, then **polymorphism** is happening.

### Example:
#### Developer.java
```java
public class Developer {
    void work() {
        System.out.println("Developer is working");
    }
    void project() {
        System.out.println("Developer is doing project");
    }
}
```
#### JavaDeveloper.java
```java
public class JavaDeveloper extends Developer {
    @Override
    void work() {
        System.out.println("Java Developer is working");
    }
    @Override
    void project() {
        System.out.println("Java Developer is doing project");
    }
}
```
#### PythonDeveloper.java
```java
public class PythonDeveloper extends Developer {
    @Override
    void work() {
        System.out.println("Python Developer is working");
    }
    @Override
    void project() {
        System.out.println("Python Developer is doing project");
    }
}
```
#### Main.java
```java
public class Main {
    public static void main(String[] args) {

        JavaDeveloper jd = new JavaDeveloper();
        accessMethod(jd);     // Passing child object

        PythonDeveloper pd = new PythonDeveloper();
        accessMethod(pd);     // Passing another child object
    }

    public static void accessMethod(Developer dev) {
        dev.work();           // Calls child overridden methods
        dev.project();
    }
}
```
#### Output
```markdown
Java Developer is working
Java Developer is doing project
Python Developer is working
Python Developer is doing project
```

