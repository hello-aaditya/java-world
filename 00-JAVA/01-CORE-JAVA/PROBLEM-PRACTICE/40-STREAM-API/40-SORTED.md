# `sorted()` Based Questions
### 1 Sort Numbers in Ascending Order
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		45, 12, 78, 23, 9, 56, 34
	);
	
	numbers.stream()
			.sorted()
			.map(n -> n + " ")
			.forEach(System.out::print);

}
```
### 2 Sort Numbers in Descending Order
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		45, 12, 78, 23, 9, 56, 34
	);
	
	numbers.stream()
			.sorted(Comparator.reverseOrder())
			.map(n -> n + " ")
			.forEach(System.out::print);

}
```
### 3 Sort Names Alphabetically
### Solution
```java
public static void main(String[] args) {
		
	List<String> names = Arrays.asList(
		"Zulu", "Alpha", "Victor", "Bravo", "Echo", "Charlie"
	);
	
	names.stream()
			.sorted()
			.map(s -> s + " ")
			.forEach(System.out::print);
}
```
### 4 Sort Names in Reverse Alphabetical Order
### Solution
```java
public static void main(String[] args) {
		
	List<String> names = Arrays.asList(
		"Zulu", "Alpha", "Victor", "Bravo", "Echo", "Charlie"
	);
	
	names.stream()
			.sorted(Comparator.reverseOrder())
			.forEach(i -> System.out.print(i + " "));

}
```
### 5 Filter and Sort Numbers
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		45, 12, 78, 23, 9, 56, 34, 67, 18
	);
	
	numbers.stream()
			.filter(n -> n > 20)
			.sorted()
			.forEach(n -> System.out.print(n + " "));

}
```
### 6 Transform and Sort Numbers
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		5, 2, 8, 3, 4, 1
	);
	
	numbers.stream()
			.map(n -> (int)Math.pow(n, 2))
			.sorted()
			.forEach(n -> System.out.print(n + " "));
}
```
### 7 Filter, Transform and Sort
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		15, 8, 23, 4, 42, 11, 30, 7
	);
	
	numbers.stream()
			.filter(n -> (n & 1) == 0)
			.map(n -> n * 10)
			.sorted(Comparator.reverseOrder())
			.forEach(n -> System.out.print(n + " "));

}
```
### 8 Sort Employees by Salary
### Solution
```java
```
### 9 Filter Employees and Sort by Salary
### Solution
```java
```
### 10 Sort Employees by Multiple Conditions
### Solution
```java
```