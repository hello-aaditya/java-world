# `max()` Based Questions
### 1 Maximum Number
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		45, 12, 89, 34, 67, 23, 91, 56
	);
	
	int maxNumber = numbers.stream()
			.max(Integer::compareTo).get();

	System.out.println(maxNumber);
}
```
### 2 Maximum Even Number
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		17, 42, 83, 64, 91, 28, 76, 55
	);
	
	int maxEvenNumber = numbers.stream()
			.filter(n -> (n & 1) == 0)
			.max(Integer::compare)
			.get();
	
	System.out.println(maxEvenNumber);
}
```
### 3 Maximum Number Greater Than 50
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		15, 42, 87, 64, 93, 28, 76, 51, 99, 36
	);
	
	int result = numbers.stream()
			.filter(n -> (n > 50) && ((n&1) == 0)) 
			.max(Comparator.naturalOrder())
			.get();
	
	System.out.println(result);
}
```
### 4 Maximum Unique Number
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		45, 78, 23, 78, 91, 45, 67, 91, 34, 89
	);

	int result = numbers.stream()
			.distinct()
			.max(Integer::compareTo).get();
	
	System.out.println(result);
}
```
### 5 Lexicographically Maximum String
### Solution
```java
public static void main(String[] args) {
	
	List<String> names = Arrays.asList(
		"Alpha", "Charlie", "Bravo", "Delta", "Echo", "Frankie"
	);
	
	String result = names.stream()
			.max(String::compareTo).get();
	
	System.out.println(result);
}
```
### 6 Longest String
### Solution
```java
public static void main(String[] args) {
	
	List<String> keywords = Arrays.asList(
		"Java", "Stream", "Collection", "Lambda", "Programming", "API"
	);
	
	String result = keywords.stream()
			.max(Comparator.comparingInt(String::length)).get();
	
	System.out.println(result);

}
```
### 7 Longest String With Tie-Breaking
### Solution
```java
public static void main(String[] args) {
	
	List<String> words = Arrays.asList(
		"Java", "Spring", "Docker", "Python", "Lambda", "Oracle"
	);
	
	String result = 
			words.stream()
			.max(Comparator.comparingInt(String::length)
					.thenComparing(Comparator.naturalOrder())
			)
			.orElse(null);

	System.out.println(result);
}
```
### 8 Maximum Number by Absolute Value
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		-45, 12, -89, 34, 67, -23, 56, -91
	);
	
	int result = numbers.stream()
			.max(
				Comparator.comparingInt(Math::abs)
			)
			.orElseThrow();
	
	
	System.out.println(result);
}
```
### 9 Maximum Even Number Greater Than 50
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		15, 42, 87, 64, 93, 28, 76, 51, 99, 36
	);
	
	int result = numbers.stream()
			.filter(n -> (n > 50) && ((n&1) == 0)) 
			.max(Comparator.naturalOrder())
			.get();
	
	System.out.println(result);
}
```
### 10 Maximum String Using Composite Rules
### Solution
```java
public static void main(String[] args) {

	List<String> words = Arrays.asList(
		"Java", "Spring", "Docker", "Lambda", "Kubernetes", 
		"Stream", "Database", "Microservices", "Orchestration"
	);
	
	String result = words.stream()
			.max(
				Comparator.comparing(String::length)
				.thenComparing(Comparator.naturalOrder())
			).get();
	
	System.out.println(result);

}
```
# `max()` Based Custom Class Questions
### 1 Highest Salary
### Solution
```java
```
### 2 Highest Employee ID
### Solution
```java
```
### 3 Highest Salary Among DEV Employees
### Solution
```java
```
### 4 Highest Paid Employee in Each Department
### Solution
```java
```
### 5 Highest Salary After Removing Duplicate Employees
### Solution
```java
```
### 6 Highest Salary With ID Tie-Breaking
### Solution
```java
```
### 7 Highest-Paid Employee Above Department Average
### Solution
```java
```
### 8 Maximum Salary Difference Between Two Employees
### Solution
```java
```
### 9 Highest-Paid Employee Per Department After Deduplication
### Solution
```java
```
### 10 
### Solution
```java
```
