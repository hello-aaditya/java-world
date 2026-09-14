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
public static void main(String[] args) {
		
	List<String> names = Arrays.asList(
		"Alpha", "Bravo", "Charlie", "Delta",
		"November", "Oscar", "Christopher"
	);
	
	names.stream()
			.filter(n -> n.length() > 5)
			.map(n -> n.toUpperCase())
			.forEach(n -> {
				System.out.print(n + " ");
			});
}
```
### 5 Even Numbers in Range → Square
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		5, 10, 15, 20, 25, 30, 35, 40, 45, 50
	);
	
	numbers.stream()
			.filter(n -> ((n & 1) == 0) && (n>=20 && n<=40))
			.map(n -> (int)Math.pow(n, 2))
			.forEach(n -> {
				System.out.print(n + " ");
			});
}
```
### 6 Employee Salary → Employee Names
### Solution
```java
package streamApi.filterAndMap;

public class Employee {
	private int id;
	private String name;
	private double salary;
	
	public Employee(
		int id,
		String name,
		double salary
	) {
		this.id = id;
		this.name = name;
		this.salary = salary;
	}
	
	public int getId() {
		return id;
	}
	
	public String getName() {
		return name;
	}
	
	public double getSalary() {
		return salary;
	}
}
```

```java
public static void main(String[] args) {
		
	List<Employee> employees = Arrays.asList(
		new Employee(101, "Alpha", 45000),
		new Employee(102, "Bravo", 65000),
		new Employee(103, "Charlie", 55000),
		new Employee(104, "Delta", 80000),
		new Employee(105, "Echo", 40000)
	);
	
	employees.stream()
			.filter(e -> e.getSalary() > 50_000)
			.map(e -> e.getName())
			.forEach(e -> {
				System.out.print(e + " ");
			});

}
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