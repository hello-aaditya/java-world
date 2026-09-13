# `filter()` Based Questions
### 1 Greater than 50
### Solution
```java
package streamApi.filter;

import java.util.Arrays;
import java.util.List;

public class GreaterThan50 {

	public static void main(String[] args) {
		
		List<Integer> numbers = Arrays.asList(10, 25, 50, 65, 80, 35, 90);
		
		numbers.stream()
				.filter(i -> i > 50)
				.forEach(i -> {
					System.out.print(i + " ");
				});
	}

}
```
### 2 Even numbers
### Solution
```java
package streamApi.filter;

import java.util.Arrays;
import java.util.List;

public class EvenNumbers {

	public static void main(String[] args) {
		
		List<Integer> numbers = Arrays.asList(11, 20, 33, 42, 55, 68, 71, 84);
		
		numbers.stream()
				.filter(i -> i % 2 == 0)
				.forEach(i -> {
					System.out.print(i + " ");
				});

	}
}
```
### 3 Strings starting with "A"
### Solution
```java
package streamApi.filter;

import java.util.Arrays;
import java.util.List;

public class NamesStartingWithA {

	public static void main(String[] args) {
		
		List<String> names = Arrays.asList("Alpha", "Bravo", "Austin", "Delta", "Alice", "Finny");
		
		names.stream()
				.filter(i -> i.startsWith("A"))
				.forEach(i -> {
					System.out.print(i + " ");
				});

	}

}
```
### 4 Range filtering
### Solution
```java
package streamApi.filter;

import java.util.Arrays;
import java.util.List;

public class NumbersInRange {

	public static void main(String[] args) {
		
		List<Integer> numbers = Arrays.asList(5, 12, 18, 25, 50, 31, 40, 47, 55, 63);
		
		numbers.stream()
				.filter(i -> i >= 20 && i<= 50)
				.forEach(i -> {
					System.out.print(i + " ");
				});

	}

}
```
### 5 String length
### Solution
```java
package streamApi.filter;

import java.util.List;
import java.util.Arrays;

public class ValidNames {

	public static void main(String[] args) {
		
		List<String> names = Arrays.asList("Alpha", null, "Alexander", "", "Gamma", null, "Finny", "Tango");
		
		names.stream()
				.filter(n -> n != null && !n.isBlank() && n.length()>=5)
				.forEach(n -> {
					System.out.print(n + " ");
				});

	}

}
```
### 6 Remove duplicates manually through filtering logic
### Solution
```java
package streamApi.filter;

import java.util.List;
import java.util.Arrays;

public class EvenNumbersGreaterThan15 {

	public static void main(String[] args) {
		
		List<Integer> numbers = Arrays.asList(10, 15, 10, 20, 25, 15, 30, 20, 35);
		
		numbers.stream()
				.filter(n -> (n > 15) && ((n & 1) == 0))
				.forEach(n -> {
					System.out.print(n + " ");
				});

	}

}
```
### 7 Employee salary filtering
### Solution
```java
package streamApi.filter;

public class Employee {
	private int id;
	private String name;
	private double salary;
	
	public Employee(
		int id,
		String name,
		double salary
	) {
		this.id = id;
		this.name = name;
		this.salary = salary;
	}
	
	public int getId() {
		return id;
	}
	
	public String getName() {
		return name;
	}
	
	public double getSalary() {
		return salary;
	}
}
```

```java
package streamApi.filter;

import java.util.Arrays;
import java.util.List;

public class HighSalaryEmployees {

	public static void main(String[] args) {
		
		List<Employee> employees = Arrays.asList(
			new Employee(101, "Alpha", 45000),
		    new Employee(102, "Victor", 65000),
		    new Employee(103, "Tango", 55000),
		    new Employee(104, "Gamma", 80000),
		    new Employee(105, "Pascal", 40000)
		);
		
		employees.stream()
				.filter(e -> e.getSalary() > 50_000.0)
				.forEach(e -> {
					System.out.print(e.getName() + " ");
				});

	}

}
```
### 8 Multiple conditions on objects
### Solution
```java
package streamApi.filter;

import java.util.Arrays;
import java.util.List;

public class EligibleEmployees {

	public static void main(String[] args) {
		
		List<Employee> employees = Arrays.asList(
				new Employee(101, "Alpha", 45000),
			    new Employee(102, "Victor", 65000),
			    new Employee(103, "Tango", 55000),
			    new Employee(104, "Gamma", 80000),
			    new Employee(105, "Pascal", 40000)
			);
		
		employees.stream()
				.filter(e -> (e.getSalary() >= 50_000.0) && ((e.getId() & 1) == 0))
				.forEach(e -> {
					System.out.print(e.getName() + " ");
				});
	}

}
```
### 9 Null + filtering
### Solution
```java
```
### 10 Real-world transaction filtering
### Solution
```java
package streamApi.filter;

public class Transaction {
	private int id;
	private String type;
	private double amount;
	private boolean successful;
	
	public Transaction (
		int id,
		String type,
		double amount,
		boolean successful
	) {
		this.id = id;
		this.type = type;
		this.amount = amount;
		this.successful = successful;
	}
	
	public int getId() {
		return id;
	}
	
	public String getType() {
		return type;
	}
	
	public double getAmount() {
		return amount;
	}
	
	public boolean getSuccessful() {
		return successful;
	}
}
```

```java
package streamApi.filter;

import java.util.Arrays;
import java.util.List;

public class SuccessfulPayments {

	public static void main(String[] args) {
		
		List<Transaction> transactions = Arrays.asList(
			    new Transaction(101, "PAYMENT", 1500, true),
			    new Transaction(102, "REFUND", 800, true),
			    new Transaction(103, "PAYMENT", 5000, false),
			    new Transaction(104, "PAYMENT", 2500, true),
			    new Transaction(105, "REFUND", 1200, false),
			    new Transaction(106, "PAYMENT", 7500, true)
			);
		
		transactions.stream()
					.filter(t -> t.getType().equals("PAYMENT")
							&& t.getSuccessful() == true
							&& t.getAmount() > 2_000)
					.forEach(t -> {
						System.out.print(t.getId() + " ");
					});
							

	}

}
```