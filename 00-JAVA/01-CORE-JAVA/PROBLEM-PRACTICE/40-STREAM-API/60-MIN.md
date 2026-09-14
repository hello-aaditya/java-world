# `min()` Based Questions
### 1 Minimum Number
### Solution
```java
public static void main(String[] args) {

	List<Integer> numbers = Arrays.asList(
		84, 37, 92, 15, 63, 48, 29, 71, 56, 22
	);

	int minimumNumber = 
	numbers.stream()
			.min(Integer::compareTo)
			.get();
	
	System.out.println(minimumNumber);
}
```
### 2 Minimum Odd Number
### Solution
```java
public static void main(String[] args) {

	List<Integer> numbers = Arrays.asList(
		84, 37, 92, 15, 63, 48, 29, 72, 56, 41
	);

	int miniOddNumber = 
		numbers.stream()
				.filter(n -> (n & 1) == 1)
				.min(Integer::compareTo)
				.get();
	
	System.out.println(miniOddNumber);
}
```
### 3 Minimum Number Greater Than 30
### Solution
```java
public static void main(String[] args) {

	List<Integer> numbers = Arrays.asList(
		12, 67, 30, 34, 89, 45, 21, 31, 56, 29
	);
	
	int miniGreaterThan30 = 
		numbers.stream()
			.filter(n -> n > 30)
			.min(Integer::compareTo)
			.get();

	System.out.println(miniGreaterThan30);
}
```
### 4 Minimum Unique Number
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		45, 23, 78, 12, 34, 23, 67, 12, 89, 45, 18, 18
	);

	int result = 
		numbers.stream()
				.distinct()
				.min(Integer::compareTo)
				.get();
	
	System.out.println(result);
			
}
```
### 5 Lexicographically Minimum String
### Solution
```java
public static void main(String[] args) {
		
	List<String> names = Arrays.asList(
		"Delta", "Charlie", "Alpha", "Echo", "Bravo", "Foxtrot"
	);

	String result = 
		names.stream()
				.min(String::compareTo)
				.get();
	
	System.out.println(result);
}
```
### 6 Shortest String
### Solution
```java
public static void main(String[] args) {
		List<String> words = Arrays.asList(
			"Programming", "Java", "Collection", "Stream", "Lambda",
			"Code", "Database", "API", "SQL", "Kubernetes"
		);

	String result = 
		words.stream()
				.min(Comparator.comparing(String::length))
				.get();
	
	System.out.println(result);
}
```
### 7 Shortest String With Tie-Breaking
### Solution
```java
public static void main(String[] args) {
	
	List<String> words = Arrays.asList(
		"Kubernetes", "XML", "Stream", "SQL", "Database",
		"JSON", "Code", "API", "Lambda", "HTML"
	);
	
	String result =
		words.stream()
				.min(Comparator.comparing(String::length)
						.thenComparing(String::compareTo)
				)
				.get();
	
	System.out.println(result);

}
```
### 8 Minimum Number by Absolute Value
### Solution
```java
public static void main(String[] args) {

	List<Integer> numbers = Arrays.asList(
		-45, 18, -8, 34, 12, -3, 27, -15, 6, -21
	);

	int result = 
		numbers.stream()
				.min(Comparator.comparingInt(Math::abs))
				.orElseThrow();
	
	System.out.println(result);
}
```
### 9 Minimum Positive Even Number
### Solution
```java
public static void main(String[] args) {

	List<Integer> numbers = Arrays.asList(
		-20, 15, 8, 42, -6, 3, 14, 0, 26, -12, 10, 7
	);

	int result =
		numbers.stream()
				.filter(n -> (n > 0) && (n & 1) == 0)
				.min(Integer::compareTo)
				.get();
	
	System.out.println(result);
}
```
### 10 Minimum String Using Composite Rules
### Solution
```java
public static void main(String[] args) {
	
	List<String> words = Arrays.asList(
		"Framework", "XML", "Spring", "SQL", "Database",
		"JSON", "HTML", "API", "Code", "Lambda",
		"Java", "Kotlin"
	);
	
	String result = 
		words.stream()
				.min(Comparator.comparingInt(String::length)
					.thenComparing(String::compareTo)
				)
				.get();
	
	System.out.println(result);
}
```
