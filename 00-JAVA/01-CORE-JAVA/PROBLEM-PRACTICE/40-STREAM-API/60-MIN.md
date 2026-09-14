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
```
### 4 Minimum Unique Number
### Solution
```java
```
### 5 Lexicographically Minimum String
### Solution
```java
```
### 6 Shortest String
### Solution
```java
```
### 7 Shortest String With Tie-Breaking
### Solution
```java
```
### 8 Minimum Number by Absolute Value
### Solution
```java
```
### 9 Minimum Positive Even Number
### Solution
```java
```
### 10 Minimum String Using Composite Rules
### Solution
```java
```
