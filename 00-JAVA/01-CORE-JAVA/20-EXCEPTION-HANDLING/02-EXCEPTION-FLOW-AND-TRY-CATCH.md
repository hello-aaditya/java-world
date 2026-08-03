# 1. DEH (*Default Exception Handler*)
DEH is the JVM’s inbuilt exception handling mechanism that prints exception details (type, message, stack trace) and terminates the program abnormally when the exception is not handled by the programmer.
## 2. UDEH (*User Defined Exception Handler*)
UDEH is the exception handling mechanism provided by the programmer using `try-catch` so that runtime exceptions can be handled in a controlled way and the program can continue its execution safely.
### 2.1 `try` and `catch` Block Syntax
```java
try {
    // risky code (chance of exception)
}
catch(Exception e) {
    // handling code
}
```
### Why we write `catch(Exception e)`?
Because the exception created by JVM is an **object**.

So in `catch`, we need a **reference variable** to hold that object.
```java
catch(Exception e)
```
Here:
- `Exception` → type/class
- `e` → reference variable that points to exception object
## `e.printStackTrace()` & `e.getMessage()`
#### 1. `e.printStackTrace();`
```java
e.printStackTrace();
```
This prints the complete error in detail:
- exception name
- message
- line number
- method call history
#### 2. `e.getMessage()`
```java
System.out.println(e.getMessage());
```
This prints only the **message/reason** of exception.
#### Program
```java
package advanced_java.exceptionHandling;



import java.util.Scanner;
public class DivisionAndArray {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		System.out.println("CONNECTION ESTABLISHED ...");
		
		try {
			// Division
			
			System.out.print("ENTER DIVIDEND: ");
			int dividend = input.nextInt();
			
			System.out.print("ENTER DIVISOR: ");
			int divisor = input.nextInt();
			
			int quotient = dividend / divisor;
			
			System.out.println(dividend + "/" + divisor + " = " + quotient);
			
			// Array
			System.out.print("ENTER ARRAY LENGTH: ");
			int size = input.nextInt();
			int[] arr = new int[size];
			
			System.out.print("ENTER INDEX NO. TO STORE A VALUE: ");
			int index = input.nextInt();
			
			System.out.print("INSERT VALUE THAT YOU WANT TO WRITE ON INDEX " + index + ": ");
			int value = input.nextInt();
			
			arr[index] = value;
			
			System.out.println("arr[" + index + "] = " + value);
		}
		catch(Exception e) {
			e.printStackTrace();
		}
		
		System.out.println("... CONNECTION TERMINATED");
		
		input.close();
	}

}
```
In this program we can get following types of exception:
##### Exception-1: ArithmeticException
```markdown
   CONNECTION ESTABLISHED...
ENTER DIVIDEND: 10
ENTER DIVISOR: 0
java.lang.ArithmeticException: / by zero
... CONNECTION TERMINATED
at input.DivisionAndArray.main(DivisionAndArray.java:22)
```
##### Exception-2: NegativeArraySizeException
```markdown
CONNECTION ESTABLISHED ...
ENTER DIVIDEND: 10
ENTER DIVISOR: 5
10/5 = 2
ENTER ARRAY LENGTH: -1
java.lang.NegativeArraySizeException: -1
	at input.DivisionAndArray.main(DivisionAndArray.java:29)
... CONNECTION TERMINATED
```
##### Exception-3: ArrayIndexOutOfBoundsException
```markdown
CONNECTION ESTABLISHED ...
ENTER DIVIDEND: 10
ENTER DIVISOR: 5
10/5 = 2
ENTER ARRAY LENGTH: 5
ENTER INDEX NO. TO STORE A VALUE: 7
INSERT VALUE THAT YOU WANT TO WRITE ON INDEX 7: 5
java.lang.ArrayIndexOutOfBoundsException: Index 7 out of bounds for length 5
... CONNECTION TERMINATED
	at input.DivisionAndArray.main(DivisionAndArray.java:37)
```

##### Observation
From the above program we can clearly understand that **one `try` block can generate multiple exceptions** depending on the user input.
In this program, the possible runtime exceptions are:
- **ArithmeticException** → when divisor is `0`
- **NegativeArraySizeException** → when array length is negative
- **ArrayIndexOutOfBoundsException** → when index is outside the array range
These are all **Runtime Exceptions (Unchecked Exceptions)**.

📌 So to handle exceptions properly, we should either:
- use a **general catch block** `catch(Exception e)` (handles all), OR
- use **multiple catch blocks** (best practice) to handle each exception separately.