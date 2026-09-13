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
```
### 8 Multiple conditions on objects
### Solution
```java
```
### 9 Null + filtering
### Solution
```java
```
### 10 Real-world transaction filtering
### Solution
```java
```