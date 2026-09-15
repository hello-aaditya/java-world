# `groupingBy()` Based Questions
### 1 Group Numbers by Even and Odd
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> transactionIds = Arrays.asList(
		101, 204, 305, 408, 512,
		617, 720, 825, 936, 1041
	);
	
	Map<String, List<Integer>> result =
		transactionIds.stream()
				.collect(Collectors.groupingBy(n -> (n & 1) == 0 ? "EVEN" : "ODD"));
	
	result.forEach((key, nums) -> {
		System.out.println(key + " = " + nums);
	});
			

}
```
### 2 Group Numbers by Remainder
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		12, 7, 15, 10, 21,
		8, 18, 25, 30, 14,
		33, 19
	);
	
	Map<Integer, List<Integer>> result =
		numbers.stream()
				.collect(Collectors.groupingBy(n -> n % 3));
	
	result.forEach((rem, nums) -> {
		System.out.println("Remainder " + rem + " = " + nums);
	});

}
```
### 3 Group Strings by Length
### Solution
```java
public static void main(String[] args) {
	
	List<String> labels = Arrays.asList(
		"API", "Java", "Spring", "SQL",
		"Cloud", "Code", "Database",
		"Git", "Linux", "Docker"
	);
	
	Map<Integer, List<String>> result =
		labels.stream()
				.collect(Collectors.groupingBy(label -> label.length()));

	result.forEach((len, words) -> {
		System.out.println(len + " = " + words);
	});
}
```
### 4 Group Words by First Character
### Solution
```java
public static void main(String[] args) {
	
	List<String> technologies = Arrays.asList(
		"Java", "JavaScript", "Jenkins",
		"Python", "PostgreSQL",
		"Docker", "Dart",
		"Kubernetes", "Kafka"
	);
	
	Map<Character, List<String>> result =
		technologies.stream()
				.collect(Collectors.groupingBy(t -> t.charAt(0)));
	
	result.forEach((firstChar, words) -> {
		System.out.println(firstChar + " = " + words);
	});

}
```
### 5 Group Numbers by Number of Digits
### Solution
```java
```
### 6 Group Words by Their First and Last Character
### Solution
```java
```
### 7 Group Strings by Their Length and Count Each Group
### Solution
```java
```
### 8 Group Numbers by Even/Odd and Find Their Sum
### Solution
```java
```
### 9 Group Words by Length and Find the Longest Word in Each Group
### Solution
```java
```
### 10 Group Words by Length and Join Them
### Solution
```java
```
