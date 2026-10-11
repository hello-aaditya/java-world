# Method
A **method** in Java is a **block of code** written inside a class that is used to **perform a specific task**.  
It runs only when it is **called/invoked**, and it may **take inputs (parameters)** and may **return an output (return value)**.
### Types of Methods in Java (Based on Parameters & Return Type):
1) **Without Parameters and Without Return Type**
2) **Without Parameters and With Return Type**
3) **With Parameters and Without Return Type**
4) **With Parameters and With Return Type**

#### 1) Without Parameters and Without Return Type
Method that **does not take any input** and **does not return any value**
**Example-1:**
```java
void greet() {
    System.out.println("Hello");
}
```
**Example-2:**
```java
void showLine() {
    System.out.println("------------");
}
```

#### 2) Without Parameters and With Return Type
Method that **does not take any input**, but it **returns a value** of a specific type using `return`.
**Example-1:**
```java
int getNumber() {
    return 10;
}
```
**Example-2:**
```java
String getName() {
    return "Nana";
}
```

#### 3) With Parameters and Without Return Type
Method that **takes input (parameters)**, but **does not return any value**.
**Example-1:**
```java
void printSquare(int n) {
    System.out.println(n * n);
}
```
**Example-2:**
```java
void greetUser(String name) {
    System.out.println("Hello " + name);
}
```

#### 4) With Parameters and With Return Type
Method that **takes input (parameters)** and also **returns a value** after processing those inputs.
**Example-1:**
```java
int add(int a, int b) {
    return a + b;
}
```
**Example-2:**
```java
boolean isEven(int n) {
    return n % 2 == 0;
}
```
> **Parameters and Arguments:**
> **P** -> Parameters, Placeholders
> **A** -> Argument, Actual Value)

[**PTO**](160-JAVA-VARIABLE.md)