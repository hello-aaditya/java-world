# How do we handle Exception?
An exception is handled by enclosing the risky code inside a `try` block and writing one or more `catch` blocks to handle specific exceptions. This prevents the program from terminating abruptly and allows normal execution to continue.
## `try-catch` block
> A `try` block is a block of code that contains statements which may throw an exception during program execution. If an exception occurs inside the `try` block, the JVM immediately stops executing the remaining statements in the `try` block and transfers control to a matching `catch` block.

## Syntax of `try-catch` block
```java
try {
	// CODE THAT MAY THROW AN EXCEPTION
	// code that may throw an exception
} catch (ExceptionType e) {
	// CODE TO HANDLE THE EXCEPTION
}
```

