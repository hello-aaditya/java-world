![](interface-milestone.drawio.svg)

---
# Types of Interface:
1. Normal Interface
2. Marker Interface -> interface w/o any method
	1. It is **Tag Interface** and it is used to mark some functionality.
	2. Clonable, Serializable, etc.
	3. Internally -> instanceof
3. Functional Interface
4. Nested Interface
## What is Functional Programming?
> Functional programming is _a programming paradigm_ where programs are constructed by applying & composing functions.

In Java 8, Functional Programming was introduced. and Functional Interface was introduced.
Functional Programming emphasize on what to do rather than how to do.
## Functional Interface
> A Functional **interface** is an interface that contains SAM (single abstract method), that's why it is also known as SAM interface.

A **functional interface** can have multiple `default` or `static` methods, but **only one abstract method** and this single abstract method can be implemented using a lambda expression.





1. The problem (code first)
2. As a result / because of this
3. The fix — same code, with a lambda
4. **Definition lands here** (plain language before terminology, as usual)
5. Why this matters practically (your interview answer, in note form)
	>Before Java 8, if I wanted to pass behavior into a method, I had to write an anonymous inner class every time — that's a lot of boilerplate for just one piece of logic. Functional interfaces solve this because they have exactly one abstract method, so a lambda can directly represent that method. On top of that, `java.util.function` already gives me ready-made ones like `Function` or `Predicate`, so in most cases I don't even need to define my own interface — I just plug in the lambda.

















---






















## Predicate
Example-1: 
```java
package com.functionalInterfacePractice;

import java.util.function.Predicate;

public class Driver {

	public static void main(String[] args) {
		
		int[] productPrice = {539, 199, 1199, 249};
		Predicate<Integer> isExpensive = (price) -> price > 499;
		
		for (int cost : productPrice) {
			if (isExpensive.test(cost)) {
				System.out.println(cost + " is expensive");
			} else {
				System.out.println(cost + " is not expensive");
			}
		}
	}

}
```
Example-2: 
```java
package com.functionalInterfacePractice;

import java.util.function.Predicate;

public class Driver {

	public static void main(String[] args) {
		String[] names = {
				"Alpha", "Bravo", "Alice", "Adam"
		};
		
		Predicate<String> isStartsFromA = (name) ->
			name.toUpperCase().startsWith("A");
			
		for (String name : names) {
			if (isStartsFromA.test(name)) {
				System.out.println(name + " Starts with \"A\"");
			} else {
				System.out.println(name + " does not start with \"A\"");
			}
		}
	}
}
```
Example-3:
```java
package com.functionalInterfacePractice;

import java.util.ArrayList;
import java.util.List;
import java.util.function.Predicate;

class Student {
	private String name;
	private int age;
	
	Student(String name, int age) {
		this.name = name;
		this.age = age;
	}

	public String getName() {
		return name;
	}

	public int getAge() {
		return age;
	}

	public void setName(String name) {
		this.name = name;
	}

	public void setAge(int age) {
		this.age = age;
	}
	
	
}

public class Driver {

	public static void main(String[] args) {
		
		List<Student> students = new ArrayList<>();
		students.add(new Student("Alpha", 12));
		students.add(new Student("Beta", 11));
		students.add(new Student("Charlie", 13));
		students.add(new Student("Delta", 13));
		
		Predicate<Integer> is13 = (age) -> age == 13;
		
		for (Student student : students) {
			if (is13.test(student.getAge())) {
				System.out.println(student.getName() + " -> " + student.getAge());
			} else {
				System.out.println(false);
			}
		}
	}
}
```
Example- 4
```java
package com.functionalInterfacePractice;

import java.util.function.Predicate;

public class Driver {

	public static void main(String[] args) {
		
		String password = "Java@avaJ123";
		
		Predicate<String> strongPassword = (givenPassword) -> 
			givenPassword.length() > 8;
			
		System.out.println(strongPassword.test(password));
	}
}
```
## Bipredicate
Example: Discount Eligibility
```java
package com.functionalInterfacePractice;

import java.util.function.BiPredicate;

public class Driver {

	public static void main(String[] args) {
		
		int mrp = 1499;
		boolean premiumMember = true;
		
		BiPredicate<Integer, Boolean> checkEligibilityForDiscount = (purchaseAmount, membership) -> 
			mrp >= 1000 && membership;
			
		System.out.println("Person is eligible for discount: " + checkEligibilityForDiscount.test(mrp, premiumMember));
	}
}
```
Login Authentication
```java
package com.functionalInterfacePractice;

import java.util.function.BiPredicate;

public class Driver {

	public static void main(String[] args) {
		
		String givenUsername = "admin";
		String givenPassword = "Java@123";
		
		BiPredicate<String, String> login = (username, password) ->
			username.equals("admin") && password.equals("Java@123");
			
		System.out.println("Log-in: " + (login.test(givenUsername, givenPassword) ? "Success" : " Fail"));
	}
}
```
## Supplier
Generate OTP:
```java
package com.functionalInterfacePractice;

import java.util.Random;
import java.util.function.Supplier;

public class Driver {

	public static void main(String[] args) {
		
		Supplier<Integer> generateOtp = () -> 1000 + new Random().nextInt(9000);
		System.out.println("OTP: " + generateOtp.get());
	}
}
```
Print Company name
```java
package com.functionalInterfacePractice;

import java.util.function.Supplier;

public class Driver {

	public static void main(String[] args) {
		
		Supplier<String> companyName = () -> "productHub";
		
		System.out.println("Company: " + companyName.get());
	}
}
```
Generate Invoice
```java
package com.functionalInterfacePractice;

import java.util.Random;
import java.util.function.Supplier;

class SerialNumber {
	public static int generateNumber() {
		int serialNumber = 1000 + new Random().nextInt(9000); 
		return serialNumber;
	}
}

public class Driver {

	
	
	public static void main(String[] args) {
		
		Supplier<String> generateInvoice = () -> 
			"PH-" + System.currentTimeMillis() + "-"+ SerialNumber.generateNumber();
			
		System.out.println(generateInvoice.get());
	}
}
```
## Consumer
Email Sender:
```java
package com.functionalInterfacePractice;

import java.util.function.Consumer;

public class Driver {

	public static void main(String[] args) {

		Consumer<String> mailSender = (emailTo) -> 
			System.out.println("Email has been sent to: " + emailTo);
			
		mailSender.accept("alphabeta@email.com");
	}
	
}
```
Update an Object:
```java
package com.functionalInterfacePractice;

import java.util.function.Consumer;

class Student {
	String name;
	
	Student(String name) {
		this.name = name;
	}
}

public class Driver {

	public static void main(String[] args) {

		Student student = new Student("Alpha");
		
		Consumer<Student> updateName = (StudentReference) -> StudentReference.name = "Beta";
		updateName.accept(student);
		
		
		System.out.println(student.name);
	}
	
}
```
## Function
Kg to Gram Conversion:
```java
package com.functionalInterfacePractice;

import java.util.function.Function;

public class Driver {

	public static void main(String[] args) {
		
		Function<Double, Double> kgToGram = (kilogram) -> 
			kilogram * 1000;
		
		double bodyWeight = 76.352;
		double gramConversion = kgToGram.apply(bodyWeight);
		
		System.out.println(
			"Body Weight (in KG): " + bodyWeight +
			"\nBody Weight (in Gram): " + gramConversion
		);
	}
	
}
```
