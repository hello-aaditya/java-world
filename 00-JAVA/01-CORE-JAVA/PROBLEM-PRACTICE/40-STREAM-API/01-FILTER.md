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
```
### 6 Remove duplicates manually through filtering logic
### Solution
```java
```
### 7 Employee salary filtering
### Solution
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