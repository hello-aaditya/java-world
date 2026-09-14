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
```
### 5 Lexicographically Maximum String
### Solution
```java
```
### 6 Longest String
### Solution
```java
```
### 7 Longest String With Tie-Breaking
### Solution
```java
```
### 8 Maximum Number by Absolute Value
### Solution
```java
```
### 9 Maximum Even Number Greater Than 50
### Solution
```java
```
### 10 Maximum String Using Composite Rules
### Solution
```java
```
