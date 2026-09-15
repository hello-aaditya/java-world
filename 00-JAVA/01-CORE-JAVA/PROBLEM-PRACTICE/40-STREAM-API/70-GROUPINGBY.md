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
public static void main(String[] args) {
	
	List<Integer> invoiceNumbers = Arrays.asList(
		42, 105, 7, 1284,
		56, 903, 12, 4501,
		86, 731, 19, 6023
	);

	invoiceNumbers.stream()
			.collect(
				Collectors.groupingBy(n -> String.valueOf(n).length())
			)
			.forEach((len, invoices) -> {
				System.out.println(len + " = " + invoices);
			});
	
}
```
### 6 Group Words by Their First and Last Character
### Solution
```java
public static void main(String[] args) {
	
	List<String> commands = Arrays.asList(
		"Build", "Bind",
		"Deploy", "Debug",
		"Commit", "Clone",
		"Push", "Pull",
		"Merge", "Move"
	);
	
	commands.stream()
			.collect(Collectors.groupingBy(command -> 
				command.charAt(0) + "-" +
				command.charAt(command.length()-1)
			))
			.forEach((firstAndLast, command) -> {
				System.out.println(firstAndLast + " = " + command);
			});

}
```
### 7 Group Strings by Their Length and Count Each Group
### Solution
```java
public static void main(String[] args) {
	
	List<String> operations = Arrays.asList(
		"GET", "POST", "PUT",
		"PATCH", "DELETE",
		"LOGIN", "LOGOUT",
		"SEARCH", "UPDATE",
		"CREATE"
	);
	
	Map<Integer, Long> result = 
		operations.stream()
				.collect(Collectors.groupingBy(op -> op.length(),
							Collectors.counting()
						)
				);

	System.out.println(result);
}
```
### 8 Group Numbers by Even/Odd and Find Their Sum
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> paymentAmounts = Arrays.asList(
		120, 75, 240, 135,
		80, 95, 310, 125,
		60, 145
	);
	
	Map<String, Integer> result =
		paymentAmounts.stream()
				.collect(Collectors.groupingBy(amount -> (amount & 1) == 0 ? "EVEN" : "ODD",
							Collectors.summingInt(amount -> amount)
						)
				);
	
	result.forEach((key, sum) -> {
		System.out.println(key + " = " + sum);
	});

}
```
### 9 Group Words by Length and Find the Longest Word in Each Group
### Solution
```java
```
### 10 Group Words by Length and Join Them
### Solution
```java
```
