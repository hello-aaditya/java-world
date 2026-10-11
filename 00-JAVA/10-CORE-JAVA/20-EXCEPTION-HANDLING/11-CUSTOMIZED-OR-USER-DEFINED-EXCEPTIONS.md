# Customized or User-Defined Exception
Sometimes too meet programming requirements we can define our own exceptions, such type of exceptions are called Customized or User-Defined Exceptions.
Example- `TooYoungException`, `TooOldException`, `InsufficientFundsException` etc.
## Syntax of Customized or User-Defined Exception
```java
class ClassName extends RuntimeException {
	// constructor
	ClassName(String message) {
		super(message);
	}
}
```
## Example
```java
class TooYoungException extends RuntimeException {
	TooYoungException(String message) {
		super(message);
	}
}

class TooOldException extends RuntimeException {
	TooOldException(String message) {
		super(message);
	}
}
```

```java
public class CustException {

	public static void main(String[] args) {
		
		int age = Integer.parseInt(args[0]);
		
		if (age < 16) {
			throw new TooYoungException("Age " + age + " is too young. Minimum age to open an account is 16.");
		} else if (age > 60) {
			throw new TooOldException("Age " + age + " exceeds maximum limit. Maximum age to open an account is 60.");
		} else {
			System.out.println("You will get account details very soon...");
		}
	}
	
}
```

- `throw` keyword is best suitable for customized or user-defined exception but not for pre-defined exceptions.
- It is highly recommended to define customized exception as **unchecked** i.e. we have to extend `RuntimeException` but not `Exception`.
- `Super(String message)` is used to make description/message available to default exception handler.