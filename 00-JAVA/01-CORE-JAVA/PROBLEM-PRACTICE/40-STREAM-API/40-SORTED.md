# `sorted()` Based Questions

### 1. Sort Numbers in Ascending Order

Given:

```java
List<Integer> numbers = Arrays.asList(45, 12, 78, 23, 9, 56, 34);
```

Use `sorted()` to print all numbers in **ascending order**.

**Expected output:**

```
9 12 23 34 45 56 78
```

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

### 2. Sort Numbers in Descending Order

Given:

```java
List<Integer> numbers = Arrays.asList(45, 12, 78, 23, 9, 56, 34);
```

Print all numbers in **descending order** using `sorted()` with a `Comparator`.

**Expected output:**

```
78 56 45 34 23 12 9
```

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

### 3. Sort Names Alphabetically

Given:

```java
List<String> names = Arrays.asList("Zulu", "Alpha", "Victor", "Bravo", "Echo", "Charlie");
```

Sort the names in **alphabetical order** and print them.

**Expected output:**

```
Alpha Bravo Charlie Echo Victor Zulu
```

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

### 4. Sort Names in Reverse Alphabetical Order

Given:

```java
List<String> names = Arrays.asList("Zulu", "Alpha", "Victor", "Bravo", "Echo", "Charlie");
```

Sort the names in **reverse alphabetical order** using `sorted()` with an appropriate `Comparator`.

**Expected output:**

```
Zulu Victor Echo Charlie Bravo Alpha
```

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

### 5. Filter and Sort Numbers

Given:

```java
List<Integer> numbers = Arrays.asList(45, 12, 78, 23, 9, 56, 34, 67, 18);
```

Select only numbers **greater than 20**, sort them in **ascending order**, and print.

**Expected output:**

```
23 34 45 56 67 78
```

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

### 6. Transform and Sort Numbers

Given:

```java
List<Integer> numbers = Arrays.asList(5, 2, 8, 3, 4, 1);
```

Square every number, sort the results in **ascending order**, and print.

**Expected output:**

```
1 4 9 16 25 64
```

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

### 7. Filter, Transform and Sort

Given:

```java
List<Integer> numbers = Arrays.asList(15, 8, 23, 4, 42, 11, 30, 7);
```

Select only **even numbers**, multiply each by `10`, sort in **descending order**, and print.

**Expected output:**

```
420 300 80 40
```

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

### Employee class

```java
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

### 8. Sort Employees by Salary

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(103, "Charlie", 65000),
    new Employee(101, "Alpha",   45000),
    new Employee(105, "Echo",    55000),
    new Employee(102, "Bravo",   75000),
    new Employee(104, "Delta",   50000)
);
```

Sort employees by **salary in ascending order** and print only their names.

**Expected output:**

```
Alpha Delta Echo Charlie Bravo
```

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

### 9. Filter Employees and Sort by Salary

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(103, "Charlie", 65000),
    new Employee(101, "Alpha",   45000),
    new Employee(105, "Echo",    55000),
    new Employee(102, "Bravo",   75000),
    new Employee(104, "Delta",   50000),
    new Employee(106, "Foxtrot", 85000)
);
```

Select employees whose salary is **at least 50,000**, sort by salary in **descending order**, and print `Name - Salary`.

**Expected output:**

```
Foxtrot - 85000.0
Bravo - 75000.0
Charlie - 65000.0
Echo - 55000.0
Delta - 50000.0
```

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

### 10. Sort Employees by Multiple Conditions

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(101, "Alpha",   60000),
    new Employee(102, "Bravo",   50000),
    new Employee(103, "Charlie", 60000),
    new Employee(104, "Delta",   70000),
    new Employee(105, "Echo",    50000),
    new Employee(106, "Foxtrot", 70000)
);
```

Sort by **salary descending**. If two employees have the **same salary**, sort those by **name alphabetically**. Print `Name - Salary`.

**Expected output:**

```
Delta - 70000.0
Foxtrot - 70000.0
Alpha - 60000.0
Charlie - 60000.0
Bravo - 50000.0
Echo - 50000.0
```

> Use `Comparator.comparing(...).reversed().thenComparing(...)`.

### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(101, "Alpha", 60000), new Employee(102, "Bravo", 50000),
		new Employee(103, "Charlie", 60000), new Employee(104, "Delta", 70000),
		new Employee(105, "Echo", 50000), new Employee(106, "Foxtrot", 70000)
	);

	employees.stream()
			.sorted(Comparator.comparing(Employee::getSalary).reversed().thenComparing(Employee::getName))
			.map(e -> e.getName() + " - " + e.getSalary())
			.forEach(System.out::println);

}
```

# `max()` Based Custom Class Questions

The `Employee` class used here has an additional `department` field:

```java
public class Employee {
	private int id;
	private String name;
	private double salary;
	private String department;

	public Employee(int id, String name, double salary, String department) {
		this.id = id;
		this.name = name;
		this.salary = salary;
		this.department = department;
	}

	public int getId() { return id; }
	public String getName() { return name; }
	public double getSalary() { return salary; }
	public String getDepartment() { return department; }
}
```

### 1. Highest Salary

Find the employee who has the **highest salary**.

**Expected output:**

```
Echo
Salary: 1500000
```

### Solution


### 2. Highest Employee ID

Find the employee having the **maximum employee ID**.

**Expected output:**

```
Hotel
ID: 1017
```

### Solution


### 3. Highest Salary Among DEV Employees

Filter only `DEV` department employees, then find the one with the **highest salary**.

**Expected output:**

```
Echo
Salary: 1500000
```

### Solution


### 4. Highest Paid Employee in Each Department

For each department, find the employee with the **highest salary**. Result is a `Map<String, Employee>`.

**Expected output:**

```
DEV  -> Echo
PROD -> Beta
QA   -> Foxtrot
UI   -> Hotel
```

### Solution


### 5. Highest Salary After Removing Duplicate Employees

The list contains duplicate employees. Remove duplicates using `distinct()`, then find the **highest-paid unique employee**.

### Solution


### 6. Highest Salary With ID Tie-Breaking

Find the employee with the **highest salary**. If multiple employees share the same highest salary, pick the one with the **smaller ID**.

**Example:**

```
Employee A -> salary = 1500000, ID = 1007
Employee B -> salary = 1500000, ID = 1012
```

Employee A wins because `1007 < 1012`.

### Solution


### 7. Highest-Paid Employee Above Department Average

For each department:
1. Calculate the average salary.
2. Keep only employees whose salary is **above that average**.
3. From those, find the one with the **maximum salary**.

Result is a `Map<String, Optional<Employee>>`.

### Solution


### 8. Maximum Salary Difference Between Two Employees

Find the **maximum possible salary difference** between any two employees.

```
Highest salary - Lowest salary = Maximum difference
```

**Expected output:**

```
700000
```

### Solution


### 9. Highest-Paid Unique Employee Per Department

Employees with the **same ID** are considered duplicates. For each department:
1. Remove duplicate employee IDs.
2. Find the employee with the highest salary.
3. If two have the same salary, pick the one with the **higher ID**.

Result is a `Map<String, Employee>`.

### Solution


### 10. Best Employee by Business Rules

Find the best employee using these priority rules in order:

1. **Highest salary** wins.
2. If tied on salary, **DEV department** wins over others.
3. If still tied, **higher employee ID** wins.

Return the complete `Employee` object.

### Solution

