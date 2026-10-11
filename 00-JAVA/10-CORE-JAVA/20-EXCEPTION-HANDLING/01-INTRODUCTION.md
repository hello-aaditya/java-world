# Introduction to Exception
## What is an Exception
>An unexpected unwanted event that disturbs normal flow of the program is called Exception.

Example: `FileNotFoundException`, `SQLException` etc.

It is highly recommended to handle exceptions and the main objective of exception handling is- **Graceful termination of the program**.

## Exception Handling
Exception Handling doesn't mean repairing an exception, we have to provide alternative way to continue rest of the program normally, is a concept of Exception Handling.

For Example- Our programming requirement is to read data from remote file locating at London at runtime if London file is not available our program should not be terminate abnormally, we have to provide some local file to continue rest of the program normally. this way of defining alternating is nothing but exception handling.

```java
try {
	Read data from remote file locating at London
} catch (FileNotFoundException e) {
	use local file & continue rest of the program normally
}
```
