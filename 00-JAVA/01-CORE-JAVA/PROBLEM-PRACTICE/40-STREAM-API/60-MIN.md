# `min()` Based Questions

### 1. Minimum Number

Given:

```java
List<Integer> numbers = Arrays.asList(84, 37, 92, 15, 63, 48, 29, 71, 56, 22);
```

Find the **minimum number** using `min()`. Do not use `sorted()`.

**Expected output:**

```
15
```

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

### 2. Minimum Odd Number

Given:

```java
List<Integer> numbers = Arrays.asList(84, 37, 92, 15, 63, 48, 29, 72, 56, 41);
```

Find the **minimum odd number**. Only odd numbers should participate. Do not use `sorted()`.

**Expected output:**

```
15
```

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

### 3. Minimum Number Greater Than 30

Given:

```java
List<Integer> numbers = Arrays.asList(12, 67, 30, 34, 89, 45, 21, 31, 56, 29);
```

Find the **smallest number strictly greater than 30**. Do not use `sorted()`.

**Expected output:**

```
31
```

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

### 4. Minimum Unique Number

Given:

```java
List<Integer> numbers = Arrays.asList(45, 23, 78, 12, 34, 23, 67, 12, 89, 45, 18, 18);
```

Remove duplicates, then find the **minimum unique value**. Do not use `sorted()`.

**Expected output:**

```
12
```

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

### 5. Lexicographically Minimum String

Given:

```java
List<String> names = Arrays.asList("Delta", "Charlie", "Alpha", "Echo", "Bravo", "Foxtrot");
```

Find the **lexicographically minimum string** using `min()`. Do not use `sorted()`.

**Expected output:**

```
Alpha
```

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

### 6. Shortest String

Given:

```java
List<String> words = Arrays.asList(
    "Programming", "Java", "Collection", "Stream", "Lambda",
    "Code", "Database", "API", "SQL", "Kubernetes"
);
```

Find the **shortest string** by length using `min()`. Do not use `sorted()`.

**Expected output:**

```
API
```

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

### 7. Shortest String With Tie-Breaking

Given:

```java
List<String> words = Arrays.asList(
    "Kubernetes", "XML", "Stream", "SQL", "Database",
    "JSON", "Code", "API", "Lambda", "HTML"
);
```

Find the **shortest string**. If multiple strings share the same minimum length, pick the **lexicographically smaller** one. Do not use `sorted()`.

**Expected output:**

```
API
```

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

### 8. Minimum Number by Absolute Value

Given:

```java
List<Integer> numbers = Arrays.asList(-45, 18, -8, 34, 12, -3, 27, -15, 6, -21);
```

Find the number with the **minimum absolute value**. Comparison must be based on `Math.abs()`. Return the original number, not its absolute value. Do not use `sorted()`.

> `-3` has absolute value `3` → so `-3` should be selected.

**Expected output:**

```
-3
```

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

### 9. Minimum Positive Even Number

Given:

```java
List<Integer> numbers = Arrays.asList(-20, 15, 8, 42, -6, 3, 14, 0, 26, -12, 10, 7);
```

Find the **smallest positive even number** (`number > 0` and `number is even`). Do not use `sorted()`.

**Expected output:**

```
8
```

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

### 10. Minimum String Using Composite Rules

Given:

```java
List<String> words = Arrays.asList(
    "Framework", "XML", "Spring", "SQL", "Database",
    "JSON", "HTML", "API", "Code", "Lambda",
    "Java", "Kotlin"
);
```

Find the minimum string — **shortest length wins**; if lengths are equal, **lexicographically smaller** wins. Use a `Comparator` with `thenComparing()`. Do not use `sorted()`.

**Expected output:**

```
API
```

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
# `min()` Based Custom Class Questions
### 1 
### Solution
