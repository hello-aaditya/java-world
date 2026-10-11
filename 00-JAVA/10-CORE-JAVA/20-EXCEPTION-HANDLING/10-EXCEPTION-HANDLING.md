## Error
Errors are serious problems that occur due to system-level failures and these are irrecoverable, such as:
1. JVM running out of memory
2. Memory Leaks
3. Stack Overflow
4. Library Incompatibility
5. Infinite Recursion
These errors are usually beyond the developer's control and should not be handled.

#### User
```java
package com.exceptionHandling.createUser;


/*
 * @author Alpha
 */

public class User {
	
	public void createUser(String username, String password) {
		System.out.println("User.createUser() START");
		
		// GENERATE THE USER-ID
		String userId = null;
		
		try {
			String country = "IN";
			System.out.println("User.createUser()... and Country is: " + country);
			
			userId = username.substring(0, 5) + "123";
			
			System.out.println("User.createUser()... and generated User-ID is: " + userId + "END");
		} catch (NullPointerException e) {
			System.out.println("User.createUser()... Username is null");
			e.getStackTrace();
		} catch (StringIndexOutOfBoundsException e) {
			System.out.println("User.createUser()... provided short username, username length must be 5 minimum");
			e.getStackTrace();
		} catch (Exception e) {
			System.out.println("User.createUser()");
			e.getStackTrace();
		}
		
		System.out.println("User.createUser()... END");
	}
}
```
#### Driver1
```java
package com.exceptionHandling;

/*
 * @author Beta
 */

import com.exceptionHandling.createUser.User;

public class Driver1 {

	public static void main(String[] args) {
		
		User user = new User(); 
		user.createUser(null, "Test^&$(");
	}

}
```

The execution flow of try-catch is-
the line where exception generates, immediately control goes in search of related catch Exception (otherwise it will abnormally terminate the program).
means if there exists some code below the line where exception occurred will be ignored.
and if we do not want to ignore that code we must use finally block.
## `finally` block
```java
package com.exceptionHandling.createUser;


/*
 * @author Alpha
 */

public class User {
	
	public void createUser(String username, String password) {
		System.out.println("User.createUser() START");
		
		// GENERATE THE USER-ID
		String userId = null;
		
		try {
			// OPEN DB CONNECTION
			System.out.println("OPEN DB-CONNECTION");
			
			String country = "IN";
			System.out.println("User.createUser()... and Country is: " + country);
			
			userId = username.substring(0, 5) + "123";
			
			System.out.println("User.createUser()... and generated User-ID is: " + userId + "END");
			
		} catch (NullPointerException e) {
			System.out.println("User.createUser()... Username is null");
			e.getStackTrace();
		} catch (StringIndexOutOfBoundsException e) {
			System.out.println("User.createUser()... provided short username, username length must be 5 minimum");
			e.getStackTrace();
		} catch (Exception e) {
			System.out.println("User.createUser()");
			e.getStackTrace();
		} finally {
			// CLOSE DB CONNECTION
			System.out.println("CLOSE DB-CONNECTION");
		}
		
		System.out.println("User.createUser()... END");
	}
}
```

> the finally block is used to run important code, whether an exception occurs or not.

>[!Note]
>The finally block always executes after the try-catch block and is often used for tasks like closing DB connections and closing.

Write a method which returns a number from try and finally. what will be returned value when we call the method?
```java
class Person {
	int code() {
		try {
			return 5;
		} finally {
			return 10;
		}
	}
}

public class temp {

	public static void main(String[] args) {
		
		System.out.println(new Person().code());
	}
	
	
}
```

#### Output
```text
10
```
because finally block overrides the value

In general when we say- NullPointerException has been thrown -> means ->
**Object of NullPointerException class has been created & thrown**.

if we are writing multiple catch-block then we can't catch higher Exception first.
hierarchy must be maintained throughout the program.
if we write higher Exception (Parent of lower Exception) first then all the exception (related) is caught by Parent only there is no need of child. means below child exceptions will become un-reachable and compiler will produce compilation-error.

if we are handling multiple exceptions by multiple catch blocks then child-specific exception should come first. if Child-specific exception is not able to handle then Parent-specific exception will handle.