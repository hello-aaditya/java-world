# `sorted()` Based Questions
### 1 Sort Numbers in Ascending Order
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		45, 12, 78, 23, 9, 56, 34
	);
	
	numbers.stream()
			.sorted()
			.map(n -> n + " ")
			.forEach(System.out::print);

}
```
### 2 Sort Numbers in Descending Order
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		45, 12, 78, 23, 9, 56, 34
	);
	
	numbers.stream()
			.sorted(Comparator.reverseOrder())
			.map(n -> n + " ")
			.forEach(System.out::print);

}
```
### 3 Sort Names Alphabetically
### Solution
```java
public static void main(String[] args) {
		
	List<String> names = Arrays.asList(
		"Zulu", "Alpha", "Victor", "Bravo", "Echo", "Charlie"
	);
	
	names.stream()
			.sorted()
			.map(s -> s + " ")
			.forEach(System.out::print);
}
```
### 4 Sort Names in Reverse Alphabetical Order
### Solution
```java
public static void main(String[] args) {
		
	List<String> names = Arrays.asList(
		"Zulu", "Alpha", "Victor", "Bravo", "Echo", "Charlie"
	);
	
	names.stream()
			.sorted(Comparator.reverseOrder())
			.forEach(i -> System.out.print(i + " "));

}
```
### 5 Filter and Sort Numbers
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		45, 12, 78, 23, 9, 56, 34, 67, 18
	);
	
	numbers.stream()
			.filter(n -> n > 20)
			.sorted()
			.forEach(n -> System.out.print(n + " "));

}
```
### 6 Transform and Sort Numbers
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		5, 2, 8, 3, 4, 1
	);
	
	numbers.stream()
			.map(n -> (int)Math.pow(n, 2))
			.sorted()
			.forEach(n -> System.out.print(n + " "));
}
```
### 7 Filter, Transform and Sort
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		15, 8, 23, 4, 42, 11, 30, 7
	);
	
	numbers.stream()
			.filter(n -> (n & 1) == 0)
			.map(n -> n * 10)
			.sorted(Comparator.reverseOrder())
			.forEach(n -> System.out.print(n + " "));

}
```
### 8 Sort Employees by Salary
### Solution
```java
package streamApi.sorted;

public class Employee {
	
	private int id;
	private String name;
	private double salary;
	
	public Employee (
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
		new Employee(103, "Charlie", 65000),
		new Employee(101, "Alpha", 45000),
		new Employee(105, "Echo", 55000),
		new Employee(102, "Bravo", 75000),
		new Employee(104, "Delta", 50000)
	);
	
	employees.stream()
			.sorted(Comparator.comparing(Employee::getSalary))
			.map(e -> e.getName())
			.forEach(e -> System.out.print(e + " "));
	
}
```
### 9 Filter Employees and Sort by Salary
### Solution
```java
	public static void main(String[] args) {
		
		List<Employee> employees = Arrays.asList(
		    new Employee(103, "Charlie", 65000),
		    new Employee(101, "Alpha", 45000),
		    new Employee(105, "Echo", 55000),
		    new Employee(102, "Bravo", 75000),
		    new Employee(104, "Delta", 50000),
		    new Employee(106, "Foxtrot", 85000)
		);

		employees.stream()
				.filter(e -> e.getSalary() >= 50_000)
				.sorted(Comparator.comparing(Employee::getSalary).reversed())
				.map(e -> e.getName() + " - " + e.getSalary())
				.forEach(System.out::println);
	}
	```
### 10 Sort Employees by Multiple Conditions
### Solution
```java
```