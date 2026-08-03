# 1. How Java Code Works (Journey: `.java` ➜ Machine Code)
We know that, a **microprocessor** can only understand **Machine Language** (0s and 1s) and a Java program is written in **high level language**, so it cannot run directly.
So the journey is:
### I. Source Code
We write code in:  **`Program.java`**
### II. Compilation
Java Compiler (**`javac`**) converts `.java` into **`Program.class`** (**Bytecode**).
### III. Execution
- JVM (Java Virtual Machine) takes `.class` file
- JVM converts bytecode into **machine code** (using JIT internally)
- Finally, CPU executes it
> `.java` ➜ (Compiler) ➜ `.class` ➜ (JVM) ➜ Machine Code ➜ Runs on CPU

# 2. Compilation-Time vs Runtime
A Java program works in **two important phases**:
a)  **Compilation-Time**
b)  **Runtime** (**Execution-Time**)

### a) Compilation-Time
Compilation Time is the phase when the **Java Compiler (`javac`)** converts the **source code (`.java`)** into **bytecode (`.class`)**.
During compilation, compiler checks for:
- syntax errors
- Java rules
- structure of the code

If the compiler finds any mistake, it **will not compile the program** and it highlights the errors so that we can fix them.
### b) Runtime (Execution Time)
Runtime (Execution Time) is the phase when the program **actually executes**.
In this phase:
- JVM loads the `.class` file (bytecode)
- JVM converts bytecode into **machine code** (internally)
- then CPU processes that machine code and produces the output

📌 Runtime errors occur during this phase, and these runtime errors are called **Exceptions**.

# 3. Errors (Compile-time Error & Runtime Error)
### a) Compilation-Time Error
**Compile-time errors** are the errors detected by the **Java compiler (JAVAC)** while compiling `.java` code into `.class` bytecode, and due to these errors the program **does not compile**.
Examples of Compilation-Time Error:
##### I) **Syntax Errors**
- Missing semicolons at the end of statements.
- Missing or mismatched parentheses, curly braces, or square brackets.
- Misspelling keywords (e.g., `Int` instead of `int`).

##### II) **Semantic Errors**
- Using a variable without declaring it.
- Type mismatches (`int number = "Java Programming is fun"`).
- Unreachable code (e.g., a statement placed after a `return` statement)
### b) Runtime Error / Exception
**Runtime errors** are the errors that occur **during program execution** after being successfully compiled.
In Java these runtime errors are called **Exceptions**.
Examples of Runtime Error:
- faulty logic
- wrong user input
- divide by zero
- array index out of range etc.

# 4. What is EXCEPTION?
In Java, an **EXCEPTION** is a runtime event that occurs during the execution of a program and disrupts its normal flow of instructions.
## 4.1 Why Handling Exception is Mandatory?
Exception Handling is mandatory because an exception is an **unwanted event** that disrupts the **normal flow of execution**.  
If we don’t handle it, then JVM’s **DEH (Default Exception Handler)** will handle it and the program will terminate suddenly.
#### Example
```java
package advance_java.exceptionHandling;

import java.util.Scanner;

public class Division {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
		
		System.out.println("EXECUTION STARTED...");
        System.out.print("ENTER DIVIDEND: ");
        int dividend = input.nextInt();

        System.out.print("ENTER DIVISOR: ");
        int divisor = input.nextInt();

        int quotient = dividend / divisor;

        System.out.println(dividend + "/" + divisor + " = " + quotient);
        
        System.out.println("... EXECUTION COMPLETED");

        input.close();
    }
}
```
If user enters `0` as divisor, then exception occurs at:
```java
int quotient = dividend / divisor;
```
After generating the exception, the program gets terminated from this line and remaining statements will not execute.  
Here, **DEH is responsible** to handle the exception.
But if we want the program to **continue execution**, then we must handle the exception using **try-catch** so that even if exception occurs, the remaining statements can still execute safely.
#### Example with `try-catch`
```java
package advance_java.exceptionHandling;

import java.util.Scanner;

public class Division {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        
		System.out.println("EXECUTION STARTED...");
		
        try {
            System.out.print("ENTER DIVIDEND: ");
            int dividend = input.nextInt();

            System.out.print("ENTER DIVISOR: ");
            int divisor = input.nextInt();

            int quotient = dividend / divisor;

            System.out.println(dividend + "/" + divisor + " = " + quotient);

        } catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero!");
        }

        System.out.println("... EXECUTION COMPLETED");

        input.close();
    }
}
```
- If user enters `0` as divisor → `ArithmeticException` occurs
- But instead of terminating the program,  the exception is caught inside `catch`
- Remaining lines **will execute normally**

📌 Meaning:
> Now **UDEH (User Defined Exception Handling)** works, not DEH.

# 5. Exception is a Class in Java
In Java, an **Exception is not just an error message**, it is actually a **class**.  
So whenever an exception occurs during runtime, JVM creates an **object** of that exception class.
**Example**
- divide by zero → `ArithmeticException` object created
- wrong array index → `ArrayIndexOutOfBoundsException` object created
## 5.1 What does JVM/Exception Handler do after Exception occurs?
When an exception is generated, JVM’s Exception Handling system **bundles all the important information** inside that exception object, like:
- **Exception name/type**
- **Reason/message** (why it occurred)
- **Line number** where it occurred
- **Method call details** (stack trace)
Then this complete information is shown on the output screen by the **Exception Handler** (Default Exception Handler).
# 6. Why Java is More Secure Than C/C++
In the early days when **C language** came into the market, computers were very costly and mostly used in **universities/government/organizations**, not like today where everyone has a personal laptop.
In C, the program is compiled into **machine-dependent native code**, and that code is executed **directly by the OS/CPU**. So if a serious runtime error occurs (like illegal memory access), the **OS has to handle it**, and if it fails then the program may crash and sometimes the whole system can become unstable or freeze.

But in **Java**, first the **compile-time errors** are handled by **JAVAC**, and after compilation it generates **bytecode (`.class`)**. This bytecode is given to the **JVM**, which provides a runtime environment and helps in identifying and handling **runtime errors (Exceptions)** in a controlled way.  
That’s why Java programs are considered more **secure, stable, and reliable** as compared to C/C++.

Note- Java doesn’t “fix” runtime errors automatically — it **handles them gracefully** using `try-catch`, instead of crashing the program suddenly.

**[PTO](02-EXCEPTION-FLOW-AND-TRY-CATCH.md)**