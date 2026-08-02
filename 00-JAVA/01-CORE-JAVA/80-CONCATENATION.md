# Concatenation
> **Concatenation** is the process of combining **strings (text)** and **variables/values** using the `+` operator to produce a single meaningful output.

## Examples
#### 1) String + String
```java
String a = "Hello";
String b = "World";

System.out.println(a + " " + b);   // Hello World
```
#### 2) String + Number
```java
int age = 20;

System.out.println("My age is " + age);  // My age is 20
```
#### 3) Number + Number + String
```java
System.out.println(10 + 20 + "Java");   // 30Java
System.out.println("Java" + 10 + 20);   // Java1020
```
**Reason:** `+` works as **addition** until a **String comes**, then it becomes **concatenation**.

[**PTO**](110-OPERATORS.md)