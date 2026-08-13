# Multi-Catch Block
Until 1.6-version even though multiple different exceptions having same handling code.
For every exception type we have to write a separate `catch` block. it increases length of the code and reduces readability.
Example:
```java
try {

} catch (ArithmeticException e) {
	e.printStackTrace();
} catch (IOException e) {
	e.printStackTrace();
} catch (NullPointerException e) {
	SOPLN(e.getMessage());
} catch (InterruptedException e) {
	SOPLN(e.getMessage());
}
```
To overcome this probem **Sun** problem introduced multi-catch block in 1.7-version. according to this we can write a single `catch` block that can handle multiple different type of exceptions.
```java
try {

} catch (ArithmeticException | IOException e) {
	e.printStackTrace();
} catch (NullPointerException | InterruptedException e) {
	SOPLN(e.getMessage());
}
```
The main advantage of this approach is- length of the code will be reduced and readability will be improved.
**Example**:
```java
public class Driver {

	public static void main(String[] args) {
		
		try {
			System.out.println(10 / 0);
			String name = null;
			System.out.println(name.length());
		} catch (ArithmeticException | NullPointerException e) {
			System.out.println(e);
		}

	}

}
```
In the above example whether raised exception is either `ArithmeticException` or `NullPointerException` the same `catch` can listen.

---
In multi catch block there should not be any relation between exception types (either child to parent or parent to child or same type) otherwise we will get compile-time error.
```java
try {

} catch (ArithmeticException | Exception e) {
	e.printStackTrace();
}
```
compile-time Error: Alternatives in a multi-catch statement cannot related by subclassing.

---
1. Exception Propagation:
	Inside a method if an exception raised and if we are not handling that exception then exception object will be propagated to caller then caller method is responsible to handle exception. this process is called **Exception Propagation**.
2. Rethrowing Exception
	We can use this approach to convert one exception type to another exception type.
	Example:
	```java
	try {
		SOPLN(10 / 0);
	} catch (ArithmeticException e) {
		throw new NullPointerException();
	}
	```