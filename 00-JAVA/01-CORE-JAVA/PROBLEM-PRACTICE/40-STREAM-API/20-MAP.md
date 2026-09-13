# `map()` Based Questions
### 1 Square Numbers
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		10, 20, 30, 40, 50
	);
	
	numbers.stream()
			.map(i -> i*i)
			.forEach(i -> {
				System.out.print(i + " ");
			});

}
```
### 2 Double Numbers
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		5, 10, 15, 20, 25
	);
	
	numbers.stream()
			.map(i -> i * 2)
			.forEach(n -> {
				System.out.print(n + " ");
			});
}
```
### 3 Convert Names to Uppercase
### Solution
```java
public static void main(String[] args) {
		
	List<String> names = Arrays.asList(
		"Alpha", "Bravo", "Austin", "Charlie", "Alice", "Delta", "Echo"
	);
	
	names.stream()
			.filter(n -> n.startsWith("A"))
			.map(n -> n.toUpperCase())
			.forEach(n -> {
				System.out.print(n + " ");
			});
}
```
### 4 Convert Names to Their Length
### Solution
```java
public static void main(String[] args) {
		
	List<String> names = Arrays.asList(
		"Alpha", "Bravo", "Charlie", "Delta", "Echo"
	);
	
	names.stream()
			.map(n -> n.length())
			.forEach(i -> {
				System.out.print(i + " ");
			});

}
```
### 5 Add 10 to Every Number
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		10, 20, 30, 40, 50
	);
	
	numbers.stream()
			.map(n -> n+10)
			.forEach(i -> {
				System.out.print(i + " ");
			});

}
```
### 6 Convert Celsius to Fahrenheit
### Solution
```java
public static void main(String[] args) {
		
	List<Double> temperatures = Arrays.asList(
		0.0, 10.0, 20.0, 30.0, 40.0);
	
	temperatures.stream()
			.map(c -> (c * 9/5) + 32)
			.forEach(t -> {
				System.out.print(t + " ");
			});

}
```
### 7 Add Prefix to Names
### Solution
### 8 Employee → Employee Name
### Solution
### 9 Employee → Salary After 10% Increment
### Solution
### 10 Employee → Formatted Employee Details
### Solution