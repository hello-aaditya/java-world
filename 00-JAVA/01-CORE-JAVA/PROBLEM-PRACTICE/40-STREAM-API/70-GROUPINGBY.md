# `groupingBy()` Based Questions

### 1. Group Numbers by Even and Odd

Given:

```java
List<Integer> transactionIds = Arrays.asList(
    101, 204, 305, 408, 512,
    617, 720, 825, 936, 1041
);
```

Group the numbers into `"EVEN"` and `"ODD"` using `Collectors.groupingBy()`. Do not manually create or populate a `Map`.

**Expected output:**

```
ODD = [101, 305, 617, 825, 1041]
EVEN = [204, 408, 512, 720, 936]
```

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

### 2. Group Numbers by Remainder

Given:

```java
List<Integer> numbers = Arrays.asList(
    12, 7, 15, 10, 21,
    8, 18, 25, 30, 14,
    33, 19
);
```

Group the numbers by their **remainder when divided by 3** using `groupingBy()`. The map key must be the calculated remainder. Do not use `partitioningBy()`.

**Expected output:**

```
Remainder 0 = [12, 15, 21, 18, 30, 33]
Remainder 1 = [7, 10, 25, 19]
Remainder 2 = [8, 14]
```

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

### 3. Group Strings by Length

Given:

```java
List<String> labels = Arrays.asList(
    "API", "Java", "Spring", "SQL",
    "Cloud", "Code", "Database",
    "Git", "Linux", "Docker"
);
```

Group the labels by their **string length** using `groupingBy()`.

**Expected output:**

```
3 = [API, SQL, Git]
4 = [Java, Code]
5 = [Cloud, Linux]
6 = [Spring, Docker]
8 = [Database]
```

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

### 4. Group Words by First Character

Given:

```java
List<String> technologies = Arrays.asList(
    "Java", "JavaScript", "Jenkins",
    "Python", "PostgreSQL",
    "Docker", "Dart",
    "Kubernetes", "Kafka"
);
```

Group the technology names by their **first character** using `groupingBy()`. Use the actual first character as the key.

**Expected output:**

```
J = [Java, JavaScript, Jenkins]
P = [Python, PostgreSQL]
D = [Docker, Dart]
K = [Kubernetes, Kafka]
```

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

### 5. Group Numbers by Number of Digits

Given:

```java
List<Integer> invoiceNumbers = Arrays.asList(
    42, 105, 7, 1284,
    56, 903, 12, 4501,
    86, 731, 19, 6023
);
```

Group the invoice numbers by their **digit count** using `groupingBy()`.

**Expected output:**

```
1 = [7]
2 = [42, 56, 12, 86, 19]
3 = [105, 903, 731]
4 = [1284, 4501, 6023]
```

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

### 6. Group Words by Their First and Last Character

Given:

```java
List<String> commands = Arrays.asList(
    "Build", "Bind",
    "Deploy", "Debug",
    "Commit", "Clone",
    "Push", "Pull",
    "Merge", "Move"
);
```

Group commands by the **combination of their first and last character** (e.g. `"Build"` → `B-d`). Do not group only by the first or only by the last character.

**Expected output:**

```
B-d = [Build, Bind]
D-y = [Deploy]
D-g = [Debug]
C-t = [Commit]
C-e = [Clone]
P-h = [Push]
P-l = [Pull]
M-e = [Merge, Move]
```

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

### 7. Group Strings by Their Length and Count Each Group

Given:

```java
List<String> operations = Arrays.asList(
    "GET", "POST", "PUT",
    "PATCH", "DELETE",
    "LOGIN", "LOGOUT",
    "SEARCH", "UPDATE",
    "CREATE"
);
```

Group by length and use a **downstream collector to count** elements in each group. Result is `Map<Integer, Long>`.

**Expected output:**

```
{3=3, 4=1, 5=2, 6=2, 8=2}
```

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

### 8. Group Numbers by Even/Odd and Find Their Sum

Given:

```java
List<Integer> paymentAmounts = Arrays.asList(
    120, 75, 240, 135,
    80, 95, 310, 125,
    60, 145
);
```

Group into `"EVEN"` and `"ODD"`, then use a **downstream collector to sum** each group. Do not manually calculate the sums.

**Expected output:**

```
EVEN = 810
ODD = 575
```

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

### 9. Group Words by Length and Find the Longest Word in Each Group

Given:

```java
List<String> terms = Arrays.asList(
    "API", "SQL", "JVM",
    "Java", "Code", "Linux",
    "Spring", "Docker", "Python",
    "Database", "Kubernetes"
);
```

Group by length and use a **downstream collector to find the lexicographically largest** word in each group.

**Expected output:**

```
3 = SQL
4 = Java
5 = Linux
6 = Spring
8 = Database
10 = Kubernetes
```

### Solution
```java
public static void main(String[] args) {

	List<String> terms = Arrays.asList(
		"API", "SQL", "JVM",
		"Java", "Code", "Linux",
		"Spring", "Docker", "Python",
		"Database", "Kubernetes"
	);
	
	terms.stream()
			.collect(
				Collectors.groupingBy(
					term -> term.length(),
					Collectors.maxBy(String::compareTo)	
				)
			)
			.forEach((len, term) -> {
				System.out.println(len + " = " + term.get());
			});

}
```

### 10. Group Words by Length and Join Them

Given:

```java
List<String> keywords = Arrays.asList(
    "Java", "SQL", "Git",
    "Spring", "Docker", "Linux",
    "API", "Kafka", "Cloud",
    "Python", "Kubernetes"
);
```

Group by length and use a **downstream collector to join** words in each group with a comma. Preserve encounter order inside each group.

**Expected output:**

```
3 = SQL,Git,API
4 = Java
5 = Linux,Kafka,Cloud
6 = Spring,Docker
7 = Python
10 = Kubernetes
```

### Solution
```java
public static void main(String[] args) {

	List<String> keywords = Arrays.asList(
		"Java", "SQL", "Git",
		"Spring", "Docker", "Linux",
		"API", "Kafka", "Cloud",
		"Python", "Kubernetes"
	);
	
	keywords.stream()
			.collect(
				Collectors.groupingBy(keyword -> keyword.length(),
						Collectors.joining(",")
				)
			).forEach((len, listOfKeyword) -> {
				System.out.println(len + " = " + listOfKeyword);
			});

}
```

### Progression

```
1.  groupingBy()
2.  calculated numeric key
3.  String property
4.  character-based key
5.  calculated classification
6.  composite classification key
7.  groupingBy() + counting()
8.  groupingBy() + summingInt()
9.  groupingBy() + maxBy()
10. groupingBy() + joining()
```
