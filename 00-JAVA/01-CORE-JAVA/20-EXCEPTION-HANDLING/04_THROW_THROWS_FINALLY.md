# 1. `throw`
The `throw` keyword in Java is used to **explicitly throw an exception** from a method or a block of code during program execution.
### Syntax
```java
throw new ExceptionType("message");
```
### Example
```java
throw new ArithmeticException("Cannot divide by zero");
```
#### Why `throw` is used?
We use `throw` when we want to:
- [1-create our own exception condition](#1-create-our-own-exception-condition)
- [2-stop execution at a point](#2-stop-execution-at-a-point)
- [3-send exception to catch block / caller](#3-send-exception-to-catch-block--caller)
### Program
```java
public class ThrowDemo {
    public static void main(String[] args) {

        int age = 15;

        if (age < 18) {
            throw new ArithmeticException("You are not eligible!");
        }

        System.out.println("You can vote.");
    }
}
```

# 2. `throws`
`throws` keyword is used to declare that a method **may generate an exception**, and the responsibility of handling it is given to the **caller method**.

> 📌 Simple line:
> 	`throws` means: _I won’t handle it here, caller will handle it._

### Syntax
```java
returnType methodName() throws ExceptionType {
    // risky code
}
```
### Example
```java
static void divide() throws ArithmeticException {
    int a = 10 / 0;
}
```
#### Important Point
If the caller also does not handle it, then finally JVM’s **DEH** will handle it and program will terminate.
### Program

---
#### 1-create our own exception condition
Sometimes Java will NOT automatically create an exception, but **we want to create one** based on our rule.
**Example**: Age should be 18+
```java
int age = 15;

if(age < 18) {
    throw new ArithmeticException("Age must be 18 or above!");
}
```
Here no exception was coming automatically,  but **we created our own condition** and threw an exception.
##### 2-stop execution at a point
When `throw` runs, program control immediately jumps out.
Example:
```java
System.out.println("Before throw");

throw new ArithmeticException("Stopped here!");

System.out.println("After throw"); // this will never execute
```
📌 So `throw` is like:
> “Stop right now and go to exception handling.”

##### 3-send exception to catch block / caller
When we throw an exception, Java searches for a handler:

→ if `try-catch` is present → goes to `catch`
→ if not present → JVM’s DEH handles and program terminates
```java
public class ThrowToCatchDemo {
    public static void main(String[] args) {

        System.out.println("1) Program Started ...");

        try {
            System.out.println("2) Inside try block");

            // Manually creating an exception
            throw new ArithmeticException("This exception is thrown manually!");

            // This line will NEVER execute
            // because control jumps to catch immediately
            System.out.println("3) After throw (This will not print)");

        } catch (ArithmeticException e) {
            System.out.println("4) Inside catch block");
            System.out.println("Handled Exception Message: " + e.getMessage());
        }

        System.out.println("5) Program Ended Normally");
    }
}
```