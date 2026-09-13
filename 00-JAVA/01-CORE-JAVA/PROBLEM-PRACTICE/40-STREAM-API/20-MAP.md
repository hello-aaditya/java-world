# `map()` Based Questions

### 1. Square Numbers

Given:

```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);
```

Using `map()`, convert every number into its **square**.

**Expected output:**

```
100 400 900 1600 2500
```

### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		10, 20, 30, 40, 50
	);
	
	numbers.stream()
			.map(i -> i*i)
			.forEach(i -> {
				System.out.print(i + " ");
			});

}
```

### 2. Double Numbers

Given:

```java
List<Integer> numbers = Arrays.asList(5, 10, 15, 20, 25);
```

Using `map()`, multiply every number by **2** and print the result.

**Expected output:**

```
10 20 30 40 50
```

### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		5, 10, 15, 20, 25
	);
	
	numbers.stream()
			.map(i -> i * 2)
			.forEach(n -> {
				System.out.print(n + " ");
			});
}
```

### 3. Convert Names to Uppercase

Given:

```java
List<String> names = Arrays.asList(
    "Alpha", "Bravo", "Austin", "Charlie", "Alice", "Delta", "Echo"
);
```

Filter only names that **start with `"A"`**, then convert them to **uppercase**.

**Expected output:**

```
ALPHA AUSTIN ALICE
```

### Solution
```java
public static void main(String[] args) {
	
	List<String> names = Arrays.asList(
		"Alpha", "Bravo", "Austin", "Charlie", "Alice", "Delta", "Echo"
	);
	
	names.stream()
			.filter(n -> n.startsWith("A"))
			.map(n -> n.toUpperCase())
			.forEach(n -> {
				System.out.print(n + " ");
			});
}
```

### 4. Convert Names to Their Length

Given:

```java
List<String> names = Arrays.asList("Alpha", "Bravo", "Charlie", "Delta", "Echo");
```

Using `map()`, convert every name into its **length**.

**Transformation:** `String -> Integer`

**Expected output:**

```
5 5 7 5 4
```

### Solution
```java
public static void main(String[] args) {
	
	List<String> names = Arrays.asList(
		"Alpha", "Bravo", "Charlie", "Delta", "Echo"
	);
	
	names.stream()
			.map(n -> n.length())
			.forEach(i -> {
				System.out.print(i + " ");
			});

}
```

### 5. Add 10 to Every Number

Given:

```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);
```

Using `map()`, add `10` to every number.

**Expected output:**

```
20 30 40 50 60
```

### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		10, 20, 30, 40, 50
	);
	
	numbers.stream()
			.map(n -> n+10)
			.forEach(i -> {
				System.out.print(i + " ");
			});

}
```

### 6. Convert Celsius to Fahrenheit

Given:

```java
List<Double> temperatures = Arrays.asList(0.0, 10.0, 20.0, 30.0, 40.0);
```

Using `map()`, convert every temperature from **Celsius to Fahrenheit**.

**Formula:** `Fahrenheit = (Celsius x 9 / 5) + 32`

**Transformation:** `Double -> Double`

**Expected output:**

```
32.0 50.0 68.0 86.0 104.0
```

### Solution
```java
public static void main(String[] args) {
	
	List<Double> temperatures = Arrays.asList(
		0.0, 10.0, 20.0, 30.0, 40.0
	);
	
	temperatures.stream()
			.map(c -> (c * 9/5) + 32)
			.forEach(t -> {
				System.out.print(t + " ");
			});

}
```

### 7. Add Prefix to Names

Given:

```java
List<String> names = Arrays.asList("Alpha", "Bravo", "Charlie", "Delta");
```

Using `map()`, add the prefix `"Employee-"` to every name.

**Expected output:**

```
Employee-Alpha Employee-Bravo Employee-Charlie Employee-Delta
```

### Solution
```java
public static void main(String[] args) {
	
	List<String> names = Arrays.asList(
		"Alpha", "Bravo", "Charlie", "Delta"
	);
	
	names.stream()
			.map(n -> "Employee-".concat(n))
			.forEach(n -> {
				System.out.print(n + " ");
			});

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

### 8. Employee -> Employee Name

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(101, "Alpha", 50000),
    new Employee(102, "Bravo", 60000),
    new Employee(103, "Charlie", 55000),
    new Employee(104, "Delta", 75000)
);
```

Using `map()`, convert every `Employee` object into its **name**.

**Transformation:** `Employee -> String`

**Expected output:**

```
Alpha Bravo Charlie Delta
```

### Solution
```java
public static void main(String[] args) {
	
	List<Employee> names = Arrays.asList(
		new Employee(101, "Alpha", 50000),
		new Employee(102, "Bravo", 60000),
		new Employee(103, "Charlie", 55000),
		new Employee(104, "Delta", 75000)	
	);
	
	names.stream()
			.map(n -> n.getName())
			.forEach(n -> System.out.print(n + " "));

}
```

### 9. Employee -> Salary After 10% Increment

Given the same `Employee` data, use `map()` to calculate the salary of every employee **after a 10% increment**.

**Transformation:** `Employee -> Double`

**Expected output:**

```
55000.0 66000.0 60500.0 82500.0
```

### Solution
```java
public static void main(String[] args) {
	
	List<Employee> names = Arrays.asList(
		new Employee(101, "Alpha", 50000),
		new Employee(102, "Bravo", 60000),
		new Employee(103, "Charlie", 55000),
		new Employee(104, "Delta", 75000)	
	);
	
	names.stream()
			.map(e -> e.getSalary() + (e.getSalary() * 0.1))
			.forEach(e -> {
				System.out.print(e + " ");
			});

}
```

### 10. Employee -> Formatted Employee Details

Given the same `Employee` data, use `map()` to convert every `Employee` into a `String` in this format:

```
ID: 101, Name: Alpha, Salary: 50000.0
ID: 102, Name: Bravo, Salary: 60000.0
ID: 103, Name: Charlie, Salary: 55000.0
ID: 104, Name: Delta, Salary: 75000.0
```

**Transformation:** `Employee -> String`

### Solution
```java
public static void main(String[] args) {

	List<Employee> names = Arrays.asList(
		new Employee(101, "Alpha", 50000),
		new Employee(102, "Bravo", 60000),
		new Employee(103, "Charlie", 55000),
		new Employee(104, "Delta", 75000)	
	);

	names.stream()
			.map(e -> "ID: " + e.getId() +
					", Name: " + e.getName() +
					", Salary: " + e.getSalary()
				)
			.forEach(e -> {
				System.out.println(e);
			});
}
```

### Progression

| #  | Difficulty | Transformation      |
| -- | ---------- | ------------------- |
| 1  | Easy       | `Integer -> Integer` |
| 2  | Easy       | `Integer -> Integer` |
| 3  | Easy       | `String -> String`   |
| 4  | Easy       | `String -> Integer`  |
| 5  | Medium     | `Integer -> Integer` |
| 6  | Medium     | `Double -> Double`   |
| 7  | Medium     | `String -> String`   |
| 8  | Hard       | `Employee -> String` |
| 9  | Hard       | `Employee -> Double` |
| 10 | Hard       | `Employee -> String` |
