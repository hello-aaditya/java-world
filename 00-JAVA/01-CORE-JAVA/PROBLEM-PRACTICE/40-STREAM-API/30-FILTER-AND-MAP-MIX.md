# Mix Questions of `filter()` and `map()`
### 1 Even Numbers → Square
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		10, 15, 20, 25, 30, 35, 40
	);
	
	numbers.stream()
			.filter(n -> (n&1) == 0)
			.map(n -> n*n)
			.forEach(n -> {
				System.out.print(n + " ");
			});
}
```
### 2 Names Starting with A → Uppercase
### Solution
```java
public static void main(String[] args) {
		
	List<String> names = Arrays.asList(
		"Alpha", "Bravo", "Charlie", "Delta", "Echo"
	);
	
	names.stream()
			.map(n -> n.toUpperCase())
			.forEach(i -> {
				System.out.print(i + " ");
			});

}
```
### 3 Numbers Greater Than 20 → Double
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		10, 15, 25, 30, 12, 40, 50
	);
	
	numbers.stream()
			.filter(n -> n > 20)
			.map(n -> n*2)
			.forEach(n -> {
				System.out.print(n + " ");
			});

}
```
### 4 Names Longer Than 5 → Uppercase
### Solution
```java
```
### 5 Even Numbers in Range → Square
### Solution
```java
```
### 6 Employee Salary → Employee Names
### Solution
```java
```
### 7 Employee → Increased Salary
### Solution
```java
```
### 8 Employee → Formatted Name + Salary
### Solution
```java
```
### 9 Successful Payment → Transaction Amount
### Solution
```java
```
### 10 Complex Employee Processing
### Solution
```java
```