# `filter()` Based Questions
### 1. Greater than 50

Given:

```java
List<Integer> numbers = Arrays.asList(10, 25, 50, 65, 80, 35, 90);
```

Print all numbers **greater than 50**.

**Expected output:**

```
65 80 90
```

### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		10, 25, 50, 65, 80, 35, 90
	);
	
	numbers.stream()
			.filter(i -> i > 50)
			.forEach(i -> {
				System.out.print(i + " ");
			});
}
```
### 2. Even numbers

Given:

```java
List<Integer> numbers = Arrays.asList(11, 20, 33, 42, 55, 68, 71, 84);
```

Print all **even numbers**.

**Expected output:**

```
20 42 68 84
```

### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		11, 20, 33, 42, 55, 68, 71, 84
	);
	
	numbers.stream()
			.filter(i -> i % 2 == 0)
			.forEach(i -> {
				System.out.print(i + " ");
			});
}
```

### 3. Strings starting with "A"

Given:

```java
List<String> names = Arrays.asList("Alpha", "Bravo", "Austin", "Delta", "Alice", "Finny");
```

Print only the names that **start with `"A"`**.

**Expected output:**

```
Alpha Austin Alice
```

### Solution
```java
public static void main(String[] args) {
		
	List<String> names = Arrays.asList(
		"Alpha", "Bravo", "Austin", "Delta", "Alice", "Finny"
	);
	
	names.stream()
			.filter(i -> i.startsWith("A"))
			.forEach(i -> {
				System.out.print(i + " ");
			});
}
```


### 4. Range filtering

Given:

```java
List<Integer> numbers = Arrays.asList(5, 12, 18, 25, 50, 31, 40, 47, 55, 63);
```

Print numbers that are **between 20 and 50, inclusive**.

**Condition:** `20 <= number <= 50`

**Expected output:**

```
25 50 31 40 47
```

### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		5, 12, 18, 25, 50, 31, 40, 47, 55, 63
	);
	
	numbers.stream()
			.filter(i -> i >= 20 && i<= 50)
			.forEach(i -> {
				System.out.print(i + " ");
			});

}
```


### 5. String length

Given:

```java
List<String> names = Arrays.asList("Alpha", null, "Alexander", "", "Gamma", null, "Finny", "Tango");
```

Print names whose length is **greater than or equal to 5 characters** (ignoring nulls and blanks).

**Expected output:**

```
Alpha Alexander Gamma Finny Tango
```

### Solution
```java
public static void main(String[] args) {
	
	List<String> names = Arrays.asList(
		"Alpha", null, "Alexander", "", "Gamma", null, "Finny", "Tango"
	);
	
	names.stream()
			.filter(n -> n != null && !n.isBlank() && n.length()>=5)
			.forEach(n -> {
				System.out.print(n + " ");
			});
}
```


### 6. Remove duplicates manually through filtering logic

Given:

```java
List<Integer> numbers = Arrays.asList(10, 15, 10, 20, 25, 15, 30, 20, 35);
```

Print only numbers that are **greater than 15 and even**.

**Expected output:**

```
20 30 20
```

**Requirement:** Use **one `filter()` condition** containing both conditions.

### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		10, 15, 10, 20, 25, 15, 30, 20, 35
	);
	
	numbers.stream()
			.filter(n -> (n > 15) && ((n & 1) == 0))
			.forEach(n -> {
				System.out.print(n + " ");
			});

}
```


### 7. Employee salary filtering

Given:

```java
class Employee {
    private int id;
    private String name;
    private double salary;
    // constructor + getters
}
```

```java
List<Employee> employees = Arrays.asList(
    new Employee(101, "Alpha", 45000),
    new Employee(102, "Victor", 65000),
    new Employee(103, "Tango", 55000),
    new Employee(104, "Gamma", 80000),
    new Employee(105, "Pascal", 40000)
);
```

Using `filter()`, print employees whose salary is **greater than Rs.50,000**. Do not create a separate salary list.

**Expected output:**

```
Victor Tango Gamma
```

### Solution
```java
package streamApi.filter;

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
		new Employee(102, "Victor", 65000),
		new Employee(103, "Tango", 55000),
		new Employee(104, "Gamma", 80000),
		new Employee(105, "Pascal", 40000)
	);
	
	employees.stream()
			.filter(e -> e.getSalary() > 50_000.0)
			.forEach(e -> {
				System.out.print(e.getName() + " ");
			});

}
```


### 8. Multiple conditions on objects

Using the same `Employee` class, print employees who satisfy **both**:

- salary `>=` 50,000
- employee ID is **even**

**Expected output:**

```
Victor Gamma
```

Because:

```
Alpha  -> 101, 45000  x salary too low
Victor -> 102, 65000  ok
Tango  -> 103, 55000  x ID is odd
Gamma  -> 104, 80000  ok
Pascal -> 105, 40000  x salary too low
```

### Solution
```java
public static void main(String[] args) {
	
	List<Employee> employees = Arrays.asList(
			new Employee(101, "Alpha", 45000),
			new Employee(102, "Victor", 65000),
			new Employee(103, "Tango", 55000),
			new Employee(104, "Gamma", 80000),
			new Employee(105, "Pascal", 40000)
		);
	
	employees.stream()
			.filter(e -> (e.getSalary() >= 50_000.0) && ((e.getId() & 1) == 0))
			.forEach(e -> {
				System.out.print(e.getName() + " ");
			});
}

```


### 9. Null + filtering

Given:

```java
List<String> names = Arrays.asList(
    "Alpha", null, "Alexander", "", "Gamma", null, "Finny", "Tango"
);
```

Print names that satisfy **all three conditions**:

1. Name is not `null`
2. Name is not empty
3. Name contains at least **5 characters**

**Expected output:**

```
Alpha Alexander Gamma Finny Tango
```

> **Important:** Your filter must not throw `NullPointerException`.

### Solution
```java
public static void main(String[] args) {
	
	List<String> names = Arrays.asList("Alpha", null, "Alexander", "", "Gamma", null, "Finny", "Tango");
	
	names.stream()
			.filter(n -> n != null && !n.isBlank() && n.length()>=5)
			.forEach(n -> {
				System.out.print(n + " ");
			});
}
```


### 10. Real-world transaction filtering

Given:

```java
class Transaction {
    private int id;
    private String type;
    private double amount;
    private boolean successful;
    // constructor + getters
}
```

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

Print only **successful PAYMENT transactions** where:

- `type` is `"PAYMENT"`
- `successful` is `true`
- `amount` is **greater than Rs.2,000**

**Expected transaction IDs:**

```
104 106
```

### Solution
```java
package streamApi.filter;

public class Transaction {
	private int id;
	private String type;
	private double amount;
	private boolean successful;
	
	public Transaction (
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
				.filter(t -> t.getType().equals("PAYMENT")
						&& t.getSuccessful() == true
						&& t.getAmount() > 2_000)
				.forEach(t -> {
					System.out.print(t.getId() + " ");
				});
}
```
