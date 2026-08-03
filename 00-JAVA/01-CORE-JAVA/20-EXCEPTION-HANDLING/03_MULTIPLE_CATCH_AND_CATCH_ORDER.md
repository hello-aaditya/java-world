# Multiple Catch Blocks
In real projects, one program can generate **different types of exceptions**, so instead of handling all exceptions in a single `catch(Exception e)`, we should use **multiple catch blocks**.
##### Advantages
- we can show **different meaningful messages** for different exceptions
- handling becomes **more clear and professional**
### Syntax: Multiple `catch`
```java
try {
    // risky code
}
catch(ArithmeticException e) {
    // handling for divide by zero
}
catch(NegativeArraySizeException e) {
    // handling for negative array size
}
catch(ArrayIndexOutOfBoundsException e) {
    // handling for invalid index
}
```
NOTE
> JVM checks `catch` blocks **top to bottom**, and the first matching catch will execute.

# General Catch Block
Sometimes we don’t know which exception can occur, or we want to handle **remaining unknown exceptions**, then we use:
```java
catch(Exception e) {
    // common handling
    e.printStackTrace();
}
```
This is called **General Catch Block**, because `Exception` is the parent class of almost all exceptions.
## Rule: General Catch Block
- When we use multiple catch blocks, the general catch block must always be written at the end.
	```java
	try {
	    // risky code
	}
	catch(ArithmeticException e) {
	    System.out.println("Divide by zero not allowed!");
	}
	catch(Exception e) {
	    System.out.println("Some exception occurred!");
	}
	```
**Reason**
Because `Exception` can catch **all exceptions**, so if it comes first, then specific catch blocks will become **unreachable**.
[Example](02-EXCEPTION-FLOW-AND-TRY-CATCH.md#Program)
