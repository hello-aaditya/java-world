# Mix Questions of `filter()` and `map()`

### 1. Even Numbers -> Square

Given:

```java
List<Integer> numbers = Arrays.asList(10, 15, 20, 25, 30, 35, 40);
```

Print the **squares of only the even numbers**.

**Expected output:**

```
100 400 900 1600
```

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

### 2. Names Starting with A -> Uppercase

Given:

```java
List<String> names = Arrays.asList("Alpha", "Bravo", "Charlie", "Delta", "Echo");
```

Convert every name to **uppercase** and print.

**Expected output:**

```
ALPHA BRAVO CHARLIE DELTA ECHO
```

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

### 3. Numbers Greater Than 20 -> Double

Given:

```java
List<Integer> numbers = Arrays.asList(10, 15, 25, 30, 12, 40, 50);
```

Find numbers **greater than 20**, double them, and print the result.

**Expected output:**

```
50 60 80 100
```

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

### 4. Names Longer Than 5 -> Uppercase

Given:

```java
List<String> names = Arrays.asList(
    "Alpha", "Bravo", "Charlie", "Delta", "November", "Oscar", "Christopher"
);
```

Filter names whose length is **greater than 5**, then convert to **uppercase**.

**Expected output:**

```
CHARLIE NOVEMBER CHRISTOPHER
```

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

### 5. Even Numbers in Range -> Square

Given:

```java
List<Integer> numbers = Arrays.asList(5, 10, 15, 20, 25, 30, 35, 40, 45, 50);
```

Filter numbers that are **even** and **between 20 and 40 inclusive**, then calculate their square.

**Expected output:**

```
400 900 1600
```

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

### 6. Employee Salary -> Employee Names

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(101, "Alpha", 45000),
    new Employee(102, "Bravo", 65000),
    new Employee(103, "Charlie", 55000),
    new Employee(104, "Delta", 80000),
    new Employee(105, "Echo", 40000)
);
```

Filter employees whose salary is **greater than 50,000**, then extract their **names**.

**Expected output:**

```
Bravo Charlie Delta
```

### Solution
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

### 7. Employee -> Increased Salary

Using the same employee data, filter employees whose salary is **greater than 50,000**, then calculate salary after a **10% increment**.

**Expected output:**

```
71500.0 60500.0 88000.0
```

### Solution
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
			.map(e -> e.getSalary() + (e.getSalary() * 0.1))
			.forEach(salary -> {
				System.out.print(salary + " ");
			});
}
```

### 8. Employee -> Formatted Name + Salary

Using the same employee data, filter employees whose salary is **greater than 50,000**, then format each as `Name - Salary`.

**Expected output:**

```
Bravo - 65000.0
Charlie - 55000.0
Delta - 80000.0
```

### Solution
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
			.filter(e -> e.getSalary() > 50_000.0)
			.map(e -> e.getName() + " - " + e.getSalary())
			.forEach(e -> {
				System.out.println(e);
			});
}
```

### Transaction class

```java
public class Transaction {
	private int id;
	private String type;
	private double amount;
	private boolean successful;

	public Transaction(
		int id,
		String type,
		double amount,
		boolean successful
	) {
		this.id = id;
		this.type = type;
		this.amount = amount;
		this.successful = successful;
	}

	public int getId() {
		return id;
	}

	public String getType() {
		return type;
	}

	public double getAmount() {
		return amount;
	}

	public boolean getSuccessful() {
		return successful;
	}
}
```

### 9. Successful Payment -> Transaction Amount

Given:

```java
List<Transaction> transactions = Arrays.asList(
    new Transaction(101, "PAYMENT", 1500, true),
    new Transaction(102, "REFUND",  800,  true),
    new Transaction(103, "PAYMENT", 5000, false),
    new Transaction(104, "PAYMENT", 2500, true),
    new Transaction(105, "REFUND",  1200, false),
    new Transaction(106, "PAYMENT", 7500, true)
);
```

Filter transactions where type is `"PAYMENT"`, successful is `true`, and amount is **greater than 2,000**. Then extract the **amount**.

**Expected output:**

```
2500.0 7500.0
```

### Solution
```java
public static void main(String[] args) {
	
	List<Transaction> transactions = Arrays.asList(
		new Transaction(101, "PAYMENT", 1500, true),
		new Transaction(102, "REFUND", 800, true),
		new Transaction(103, "PAYMENT", 5000, false),
		new Transaction(104, "PAYMENT", 2500, true),
		new Transaction(105, "REFUND", 1200, false),
		new Transaction(106, "PAYMENT", 7500, true)
	);
	
	transactions.stream()
			.filter(t -> t.getType().equals("PAYMENT") && 
					t.getSuccessful() && 
					t.getAmount() > 2_000
				)
			.map(t -> t.getAmount())
			.forEach(amt -> {
				System.out.print(amt + " ");
			});
}
```

### 10. Complex Employee Processing

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(101, "Alpha",   45000),
    new Employee(102, "Bravo",   65000),
    new Employee(103, "Charlie", 55000),
    new Employee(104, "Delta",   80000),
    new Employee(105, "Echo",    40000),
    new Employee(106, "Foxtrot", 70000)
);
```

Filter employees whose salary is **>= 60,000** and employee ID is **even**. Then format each as `Name -> Salary`.

**Expected output:**

```
Bravo -> 65000.0
Delta -> 80000.0
Foxtrot -> 70000.0
```

### Solution
```java
public static void main(String[] args) {
	
	List<Employee> employees = Arrays.asList(
		new Employee(101, "Alpha", 45000),
		new Employee(102, "Bravo", 65000),
		new Employee(103, "Charlie", 55000),
		new Employee(104, "Delta", 80000),
		new Employee(105, "Echo", 40000),
		new Employee(106, "Foxtrot", 70000)
	);
	
	employees.stream()
			.filter(e -> ( e.getSalary() >= 60_000.0 ) &&
					     ( (e.getId() & 1) == 0 )
					)
			.map(e -> e.getName() + " \u2192 " + e.getSalary())
			.forEach(val -> {
				System.out.println(val);
			});

}
```

### Progression

| #  | Level    | `filter()`                      | `map()`                     |
| -- | -------- | ------------------------------- | --------------------------- |
| 1  | Easy     | Even                            | Square                      |
| 2  | Easy     | -                               | Uppercase                   |
| 3  | Easy     | > 20                            | Double                      |
| 4  | Moderate | Length > 5                      | Uppercase                   |
| 5  | Moderate | Even + range                    | Square                      |
| 6  | Moderate | Salary > 50K                    | Employee -> Name            |
| 7  | Moderate | Salary > 50K                    | Employee -> Increased salary |
| 8  | Hard     | Salary > 50K                    | Employee -> Formatted String |
| 9  | Hard     | Multiple transaction conditions | Transaction -> Amount        |
| 10 | Hard     | Multiple employee conditions    | Employee -> Formatted String |
