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
```
### 3 Group Strings by Length
### Solution
```java
```
### 4 Group Words by First Character
### Solution
```java
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
