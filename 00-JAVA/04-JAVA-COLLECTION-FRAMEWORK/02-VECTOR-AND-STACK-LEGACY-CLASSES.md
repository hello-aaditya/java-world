# Vector and Stack: Legacy Classes in Java
## 1️. Introduction – Why do we need Vector and Stack?
While working with programs, **we often need to store data in a proper order** and access it later when required.
For example:
- While writing notes in an app, **we keep adding new points**
    - We want the notes to remain in the **same order**
    - We may want to read an earlier point again
- While writing code, **we may accidentally delete a line**
    - We want to **undo only the last action**, not everything

In both situations, **we clearly need**:
- Data to be **stored safely**
- Data to be **retrieved in a specific order**
- In some cases, the **last inserted item to come out first**, such as in an undo operation

To handle these requirements, **Java provides different data structures**.

Among the **earliest data structures introduced in Java** are:
- **Vector**
- **Stack**

These classes were introduced in the **initial versions of Java** and were widely used before modern collection classes were available.

Even though **we do not use them much in new programs today**, they are still important because:
- We may encounter them while reading **old (legacy) Java code**
- We can understand:
    - ordered data storage
    - dynamic size collections
    - basic thread safety concepts
    - LIFO behavior in Stack

So, before moving to modern collection classes, **we should clearly understand Vector and Stack** and the problem they were designed to solve.

## 1.1. What is Vector
> A **Vector** is a class in Java that is used to **store multiple elements in a single collection**.

### What Vector does
- We can store **any number of elements**
- The elements are stored in the **same order** in which we add them
- We do **not need to fix the size** of the Vector in advance
- The size of the Vector **automatically increases or decreases** based on the number of elements

Because of this behavior, **we can call Vector a dynamic array**.
### Important Features of Vector
#### 1. Dynamic Size
>In Vector, **we do not worry about the size**.
>- When we add more elements, Vector **automatically grows**
>- When we remove elements, Vector **shrinks if required**

This makes Vector easy to use when **we do not know in advance how much data we will store**.
#### 2. Maintains Insertion Order
>Vector stores elements in the **same order** in which we insert them.
>- First inserted element stays first
>- Last inserted element stays last

So, **when we retrieve elements**, they come out in the same sequence.
#### 3. Thread-Safe by Default
>Vector is **thread-safe**, which means:
>- When multiple parts of a program access the Vector at the same time,
>- Vector ensures that **only one operation happens at a time**

Because of this, **we do not face data inconsistency issues** in multi-threaded programs.
#### 4. Legacy Class
>Vector was introduced in **Java 1.0**, which is why it is considered a **legacy class**.
>- It was widely used **before Java 1.2**  
>- Later, the Collections Framework introduced better alternatives like `ArrayList`  

Even though **we rarely use Vector in new programs**, we still find it in **old Java applications**.

##### Example:
```java
Vector<Integer> v = new Vector<>();

v.add(10);
v.add(20);
v.add(30);

System.out.println(v);  // [10, 20, 30]
```
In this example:
- We did not set any size
- Vector handled resizing automatically
- Elements remained in insertion order
## 1.1. What is Stack
> A **Stack** is a class in Java that is used to store elements, but it follows a **specific order of access**.
### Basic Idea of Stack
Stack works on the **LIFO principle**:
> **Last In, First Out**

This means:
- The element that is **added last** will be **removed first**
- The element that is **added first** will be **removed last**

Because of this behavior, **Stack is very useful when we want to track recent actions**, such as undo operations.
### Relationship between Stack and Vector
Stack is **not an independent class**.
- Stack **extends Vector**
- This means Stack **inherits all the properties of Vector**

So, in Stack:
- We get **dynamic size**
- We get **insertion order storage**
- We get **thread safety**
- We get **legacy behavior**

On top of this, Stack adds its **LIFO functionality**.
### Common Stack Operations
Some commonly used operations in Stack are:
- `push()` → used to add an element on the top of the Stack
- `pop()` → used to remove the top element from the Stack
- `peek()` → used to see the top element without removing it
##### Example:
```java
Stack<String> stack = new Stack<>();

stack.push("A");
stack.push("B");
stack.push("C");

System.out.println(stack.pop());  // C
```
In this example:
- We added elements in the order: A → B → C
- The last inserted element **C** was removed first
- This clearly shows **LIFO behavior**
### Why Stack is Useful
Stack is useful in situations where:
- We want to **undo the last action**
- We want to process **recent data first**
- We want a structure where **order of removal matters**
# 2. Why Vector and Stack are called Legacy Classes
Vector and Stack are referred to as **legacy classes** in Java.
## What does “Legacy” mean?
In Java, **legacy classes** are those classes that:
- Were introduced in the **early versions of Java**
- Were used widely **before the Collections Framework (Java 1.2)**
- Are still available, but **not preferred in new programs**
## Why we do not prefer Vector and Stack today
Even though Vector and Stack still work correctly, **we usually avoid using them in new programs**.

The main reasons are:
### 1. Synchronization Overhead
Vector and Stack are **thread-safe by default**.
- Every operation is synchronized
- Only one thread can access the object at a time

Because of this:
- Programs become **slower**
- Performance decreases even when **thread safety is not required**

So, we end up paying a **performance cost unnecessarily**.
### 2. Better Alternatives are Available
With the introduction of the Collections Framework, Java provided:
- `ArrayList`
- `LinkedList`
- `Deque`

These classes:
- Are **faster**
- Give **more control**
- Allow us to **add thread safety only when needed**
### 3. Modern Concurrency Support
In modern Java, **we have better ways to handle multi-threading**, such as:
- Synchronized wrappers
- Concurrent collections

Because of this, **we no longer depend on Vector or Stack for thread safety**.
# 3. Thread Safety in Vector and Stack
To understand Vector and Stack properly, **we must understand the idea of thread safety**.
# 3.1 What does Thread-Safe mean?
A program can have **multiple threads running at the same time**.

Thread-safe means:
- When multiple threads access the same data,
- The data remains **consistent and safe**
- No unexpected or incorrect results occur
## 3.2 How Vector provides Thread Safety
Vector is **thread-safe by default**.

This means:
- Every method of Vector is **synchronized**
- When one thread is performing an operation,
- Other threads must **wait until the operation finishes**

So, at any given time:
- Only **one thread** can read or modify the Vector
#### Example
```java
Vector<Integer> v = new Vector<>();

v.add(10);
v.add(20);

int value = v.get(0);
```
In this example:
- Even if multiple threads are running,
- Vector ensures that **only one operation happens at a time**
- This prevents data corruption
## 3.3 How Stack provides Thread Safety
Stack **extends Vector**.

Because of this:
- Stack automatically becomes **thread-safe**
- All Stack operations like `push()`, `pop()`, and `peek()` are synchronized
#### Example
```java
Stack<String> stack = new Stack<>();

stack.push("Java");
stack.push("Python");

String top = stack.pop();
```
In this example:
- The `push()` and `pop()` operations are synchronized
- We do not need to add extra code for thread safety
## 3.4 Drawback of Built-in Thread Safety
Although thread safety is useful, it also has a **disadvantage**.
- Synchronization causes **performance overhead**
- Even in single-threaded programs, locking still happens
- This makes Vector and Stack **slower than modern collections**

So, **we get safety, but at the cost of speed**.