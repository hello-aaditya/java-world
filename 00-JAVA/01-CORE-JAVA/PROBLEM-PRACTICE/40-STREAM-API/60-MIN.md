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

### Employee class

```java
public class Employee {
	
	private long id;
	private String name;
	private String department;
	private double salary;
	
	public Employee (
		long id,
		String name,
		String department,
		double salary
	) {
		this.id = id;
		this.name = name;
		this.department = department;
		this.salary = salary;
	}
	
	public long getId() {
		return id;
	}
	
	public String getName() {
		return name;
	}
	
	public String getDepartment() {
		return department;
	}
	
	public double getSalary() {
		return salary;
	}
}
```

### 1. Minimum Salary Employee

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(101, "Alpha",   "DEV",   850000),
    new Employee(102, "Bravo",   "QA",    720000),
    new Employee(103, "Charlie", "DEV",   950000),
    new Employee(104, "Delta",   "UI",    680000),
    new Employee(105, "Echo",    "PROD",  810000),
    new Employee(106, "Foxtrot", "QA",    760000)
);
```

Find the employee with the **lowest salary** using `min()`. Do not use `sorted()`.

**Expected output:**

```
Delta -> 680000.0
```

### Solution
```java
public static void main(String[] args) {
	
	List<Employee> employees = Arrays.asList(
		new Employee(101, "Alpha", "DEV", 850000),
		new Employee(102, "Bravo", "QA", 720000),
		new Employee(103, "Charlie", "DEV", 950000),
		new Employee(104, "Delta", "UI", 680000),
		new Employee(105, "Echo", "PROD", 810000),
		new Employee(106, "Foxtrot", "QA", 760000)
	);
	
	Employee e =
	employees.stream()
			.min(Comparator.comparingDouble(Employee::getSalary))
			.get();

	System.out.println(e.getName() + " -> " + e.getSalary());
}
```

### 2. Minimum Employee ID

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(105, "Alpha",   "DEV",   900000),
    new Employee(102, "Bravo",   "QA",   1100000),
    new Employee(109, "Charlie", "PROD",  850000),
    new Employee(101, "Delta",   "UI",   1250000),
    new Employee(107, "Echo",    "DEV",   950000),
    new Employee(104, "Foxtrot", "QA",   1050000)
);
```

Find the employee with the **smallest employee ID**. Return the complete `Employee` object.

**Expected output:**

```
101 -> Delta
```

### Solution
```java
public static void main(String[] args) {
	
	List<Employee> employees = Arrays.asList(
		new Employee(105, "Alpha", "DEV", 900000),
		new Employee(102, "Bravo", "QA", 1100000),
		new Employee(109, "Charlie", "PROD", 850000),
		new Employee(101, "Delta", "UI", 1250000),
		new Employee(107, "Echo", "DEV", 950000),
		new Employee(104, "Foxtrot", "QA", 1050000)
	);
	
	Employee e = 
		employees.stream()
				.min(Comparator.comparingLong(Employee::getId))
				.get();
	
	System.out.println(e.getId() + " -> " + e.getName() );

}
```

### 3. Lowest Salary Among QA Employees

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(201, "Alpha",   "DEV",    700000),
    new Employee(202, "Bravo",   "QA",     850000),
    new Employee(203, "Charlie", "PROD",  1200000),
    new Employee(204, "Delta",   "QA",     680000),
    new Employee(205, "Echo",    "UI",     950000),
    new Employee(206, "Foxtrot", "QA",     720000),
    new Employee(207, "Golf",    "DEV",    900000)
);
```

Filter only `QA` employees, then find the one with the **lowest salary**. Handle the case where no QA employee exists.

**Expected output:**

```
Delta -> QA -> 680000.0
```

### Solution
```java
public static void main(String[] args) {
	
	List<Employee> employees = Arrays.asList(
		new Employee(201, "Alpha", "DEV", 700000),
		new Employee(202, "Bravo", "QA", 850000),
		new Employee(203, "Charlie", "PROD", 1200000),
		new Employee(204, "Delta", "QA", 680000),
		new Employee(205, "Echo", "UI", 950000),
		new Employee(206, "Foxtrot", "QA", 720000),
		new Employee(207, "Golf", "DEV", 900000)
	);
	
	Employee emp =
		employees.stream()
				.filter(e -> e.getDepartment().equals("QA"))
				.min(Comparator.comparingDouble(Employee::getSalary))
				.get();

	System.out.println(
		emp.getName() + " -> " + 
		emp.getDepartment() + " -> " + 
		emp.getSalary()
	);
}
```

### 4. Lowest Salary Above a Salary Threshold

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(301, "Alpha",   "DEV",   780000),
    new Employee(302, "Bravo",   "QA",    820000),
    new Employee(303, "Charlie", "PROD",  950000),
    new Employee(304, "Delta",   "UI",    800000),
    new Employee(305, "Echo",    "DEV",   860000),
    new Employee(306, "Foxtrot", "QA",    810000),
    new Employee(307, "Golf",    "PROD",  760000)
);
```

Find the employee with the **lowest salary strictly greater than 800,000**. Employees with salary `<= 800000` must be excluded.

**Expected output:**

```
Foxtrot -> 810000.0
```

### Solution
```java
public static void main(String[] args) {
	
	List<Employee> employees = Arrays.asList(
		new Employee(301, "Alpha", "DEV", 780000),
		new Employee(302, "Bravo", "QA", 820000),
		new Employee(303, "Charlie", "PROD", 950000),
		new Employee(304, "Delta", "UI", 800000),
		new Employee(305, "Echo", "DEV", 860000),
		new Employee(306, "Foxtrot", "QA", 810000),
		new Employee(307, "Golf", "PROD", 760000)
	);
	
	Employee e = 
		employees.stream()
				.filter(emp -> emp.getSalary() > 8_00_000.0)
				.min(Comparator.comparingDouble(Employee::getSalary))
				.get();

	System.out.println(e.getName() + " -> " + e.getSalary());
}
```

### 5. Lowest Salary With ID Tie-Breaker

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(405, "Alpha",   "DEV",   750000),
    new Employee(402, "Bravo",   "QA",    680000),
    new Employee(409, "Charlie", "PROD",  820000),
    new Employee(401, "Delta",   "UI",    680000),
    new Employee(407, "Echo",    "DEV",   680000),
    new Employee(404, "Foxtrot", "QA",    760000)
);
```

Find the employee with the **lowest salary**. If multiple employees share the same lowest salary, pick the one with the **smaller ID**.

> Three employees tie at 680000 — Bravo (402), Delta (401), Echo (407). 
> Smaller ID wins → **Delta**.

**Expected output:**

```
401 -> Delta -> 680000.0
```

### Solution
```java
public static void main(String[] args) {
	
	List<Employee> employees = Arrays.asList(
		new Employee(405, "Alpha", "DEV", 750000),
		new Employee(402, "Bravo", "QA", 680000),
		new Employee(409, "Charlie", "PROD", 820000),
		new Employee(401, "Delta", "UI", 680000),
		new Employee(407, "Echo", "DEV", 680000),
		new Employee(404, "Foxtrot", "QA", 760000)
	);
	
	Employee e = 
		employees.stream()
				.min(Comparator.comparingDouble(Employee::getSalary)
					.thenComparingLong(Employee::getId)
				)
				.get();

	System.out.println(
		e.getId() + " -> " +
		e.getName() + " -> " +
		e.getSalary()
	);
}
```

### 6. Lowest Salary in Each Department

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(501, "Alpha",   "DEV",  950000),
    new Employee(502, "Bravo",   "DEV",  720000),
    new Employee(503, "Charlie", "DEV",  850000),

    new Employee(504, "Delta",   "QA",   680000),
    new Employee(505, "Echo",    "QA",   820000),
    new Employee(506, "Foxtrot", "QA",   750000),

    new Employee(507, "Golf",    "PROD", 1100000),
    new Employee(508, "Hotel",   "PROD",  900000),
    new Employee(509, "India",   "PROD",  980000),

    new Employee(510, "Juliett", "UI",   650000),
    new Employee(511, "Kilo",    "UI",   780000),
    new Employee(512, "Lima",    "UI",   700000)
);
```

For each department, find the employee with the **lowest salary**. Result is a `Map<String, Optional<Employee>>`.

**Expected output:**

```
DEV  -> Bravo
QA   -> Delta
PROD -> Hotel
UI   -> Juliett
```

### Solution
```java
public static void main(String[] args) {
	
	List<Employee> employees = Arrays.asList(
		new Employee(501, "Alpha", "DEV", 950000),
		new Employee(502, "Bravo", "DEV", 720000),
		new Employee(503, "Charlie", "DEV", 850000),

		new Employee(504, "Delta", "QA", 680000),
		new Employee(505, "Echo", "QA", 820000),
		new Employee(506, "Foxtrot", "QA", 750000),

		new Employee(507, "Golf", "PROD", 1100000),
		new Employee(508, "Hotel", "PROD", 900000),
		new Employee(509, "India", "PROD", 980000),

		new Employee(510, "Juliett", "UI", 650000),
		new Employee(511, "Kilo", "UI", 780000),
		new Employee(512, "Lima", "UI", 700000)
	);
	
	Map<String, Optional<Employee>> result =
		employees.stream()
				.collect(
					Collectors.groupingBy(Employee::getDepartment,
						Collectors.minBy(
							Comparator.comparing(Employee::getSalary)
						)
					)
				);
	result.forEach((dept, e) -> {
		System.out.println(dept + " -> " + e.get().getName());
	});
}
```

### Employee1 class (Q7 and Q8)

```java
public class Employee1 {
	
	private long id;
	private String name;
	private String department;
	private double salary;
	private int age;
	
	public Employee1 (
		long id,
		String name,
		String department,
		double salary,
		int age
	) {
		this.id = id;
		this.name = name;
		this.department = department;
		this.salary = salary;
		this.age = age;
	}
	
	public long getId() {
		return id;
	}
	
	public String getName() {
		return name;
	}
	
	public String getDepartment() {
		return department;
	}
	
	public double getSalary() {
		return salary;
	}
	
	public int getAge() {
		return age;
	}
}
```

### 7. Youngest Employee Among Eligible Employees

Given:

```java
List<Employee1> employees = Arrays.asList(
    new Employee1(601, "Alpha",   "DEV",   750000, 24),
    new Employee1(602, "Bravo",   "QA",    850000, 29),
    new Employee1(603, "Charlie", "PROD",  900000, 26),
    new Employee1(604, "Delta",   "DEV",   800000, 23),
    new Employee1(605, "Echo",    "UI",   1200000, 31),
    new Employee1(606, "Foxtrot", "QA",    820000, 25),
    new Employee1(607, "Golf",    "DEV",   780000, 21),
    new Employee1(608, "Hotel",   "PROD",  950000, 27)
);
```

Filter employees whose salary is `>= 800000`, then find the **youngest** (minimum age) among them.

> Golf (age 21) is excluded because salary `780000 < 800000`.

**Expected output:**

```
Delta -> Age 23 -> Salary 800000.0
```

### Solution
```java
public static void main(String[] args) {
	
	List<Employee1> employees = Arrays.asList(
		new Employee1(601, "Alpha", "DEV", 750000, 24),
		new Employee1(602, "Bravo", "QA", 850000, 29),
		new Employee1(603, "Charlie", "PROD", 900000, 26),
		new Employee1(604, "Delta", "DEV", 800000, 23),
		new Employee1(605, "Echo", "UI", 1200000, 31),
		new Employee1(606, "Foxtrot", "QA", 820000, 25),
		new Employee1(607, "Golf", "DEV", 780000, 21),
		new Employee1(608, "Hotel", "PROD", 950000, 27)
	);

	Employee1 e =
		employees.stream()
				.filter(emp -> emp.getSalary() >= 8_00_000.0)
				.min(Comparator.comparing(Employee1::getAge))
				.get();
	
	System.out.println(
		e.getName() + " -> " +
		"Age " + e.getAge() + " -> " +
		"Salary " + e.getSalary()
	);
}
```

### 8. Minimum Salary Among Experienced Employees

Given:

```java
List<Employee1> employees = Arrays.asList(
    new Employee1(701, "Alpha",   "DEV",   950000, 28),
    new Employee1(702, "Bravo",   "QA",    780000, 32),
    new Employee1(703, "Charlie", "PROD", 1250000, 35),
    new Employee1(704, "Delta",   "DEV",   820000, 31),
    new Employee1(705, "Echo",    "UI",    700000, 27),
    new Employee1(706, "Foxtrot", "QA",    760000, 30),
    new Employee1(707, "Golf",    "PROD",  900000, 29),
    new Employee1(708, "Hotel",   "UI",    850000, 34)
);
```

An employee is **experienced** if `age >= 30`. Find the experienced employee with the **minimum salary**.

**Expected output:**

```
Foxtrot -> Age 30 -> Salary 760000.0
```

### Solution
```java
public static void main(String[] args) {
	
	List<Employee1> employees = Arrays.asList(
		new Employee1(701, "Alpha", "DEV", 950000, 28),
		new Employee1(702, "Bravo", "QA", 780000, 32),
		new Employee1(703, "Charlie", "PROD", 1250000, 35),
		new Employee1(704, "Delta", "DEV", 820000, 31),
		new Employee1(705, "Echo", "UI", 700000, 27),
		new Employee1(706, "Foxtrot", "QA", 760000, 30),
		new Employee1(707, "Golf", "PROD", 900000, 29),
		new Employee1(708, "Hotel", "UI", 850000, 34)
	);
	
	Employee1 e =
		employees.stream()
				.filter(emp -> emp.getAge() >= 30)
				.min(Comparator.comparingDouble(Employee1::getSalary)).get();
			
	System.out.println(
		e.getName() + " -> " +
		"Age " + e.getAge() + " -> " +
		"Salary " + e.getSalary()
	);
		
}
```

### 9. Minimum Salary Per Department With Tie-Breaker

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(801, "Alpha",   "DEV",  700000),
    new Employee(805, "Bravo",   "DEV",  650000),
    new Employee(803, "Charlie", "DEV",  650000),

    new Employee(806, "Delta",   "QA",   720000),
    new Employee(809, "Echo",    "QA",   680000),
    new Employee(807, "Foxtrot", "QA",   680000),

    new Employee(811, "Golf",    "PROD", 900000),
    new Employee(814, "Hotel",   "PROD", 850000),
    new Employee(812, "India",   "PROD", 850000),

    new Employee(816, "Juliett", "UI",   600000),
    new Employee(819, "Kilo",    "UI",   580000),
    new Employee(817, "Lima",    "UI",   580000)
);
```

For each department, find the employee with the **lowest salary**. If two share the same minimum salary, pick the one with the **higher ID**. Result is a `Map<String, Optional<Employee>>`.

> DEV: Bravo (805) and Charlie (803) both at 650000 — higher ID wins → Bravo.

**Expected output:**

```
DEV  -> Bravo   -> ID 805 -> 650000.0
QA   -> Echo    -> ID 809 -> 680000.0
PROD -> Hotel   -> ID 814 -> 850000.0
UI   -> Kilo    -> ID 819 -> 580000.0
```

### Solution
```java
	public static void main(String[] args) {
		
		List<Employee> employees = Arrays.asList(
		    new Employee(801, "Alpha", "DEV", 700000),
		    new Employee(805, "Bravo", "DEV", 650000),
		    new Employee(803, "Charlie", "DEV", 650000),

		    new Employee(806, "Delta", "QA", 720000),
		    new Employee(809, "Echo", "QA", 680000),
		    new Employee(807, "Foxtrot", "QA", 680000),

		    new Employee(811, "Golf", "PROD", 900000),
		    new Employee(814, "Hotel", "PROD", 850000),
		    new Employee(812, "India", "PROD", 850000),

		    new Employee(816, "Juliett", "UI", 600000),
		    new Employee(819, "Kilo", "UI", 580000),
		    new Employee(817, "Lima", "UI", 580000)
		);
		
		Map<String, Optional<Employee>> result = 
				employees.stream()
						.collect(
							Collectors.groupingBy(
								Employee::getDepartment,
								Collectors.minBy(
									Comparator.comparingDouble(Employee::getSalary)
										.thenComparing(
												Comparator.comparingLong(Employee::getId)
													.reversed()
										)
								)
							)
						);
		
		result.forEach((dept, e) -> {
			System.out.println(
				dept + " -> " +
				e.get().getName() + " -> " +
				"ID " + e.get().getId() + " -> " +
				e.get().getSalary()
			);
		});

	}
```

### 10. Minimum Salary With Composite Business Rules

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(901, "Alpha",   "QA",    600000),
    new Employee(902, "Bravo",   "PROD",  600000),
    new Employee(903, "Charlie", "DEV",   600000),
    new Employee(904, "Delta",   "DEV",   600000),
    new Employee(905, "Echo",    "UI",    650000),
    new Employee(906, "Foxtrot", "QA",    580000),
    new Employee(907, "Golf",    "DEV",   580000),
    new Employee(908, "Hotel",   "DEV",   580000),
    new Employee(909, "India",   "PROD",  580000),
    new Employee(910, "Juliett", "QA",    700000)
);
```

Find the best employee using these priority rules in order:
1. **Lowest salary** wins.
2. If tied, **DEV department** wins over others.
3. If still tied, **lower employee ID** wins.

> Lowest salary: Foxtrot (QA), Golf (DEV), Hotel (DEV), India (PROD). DEV wins → Golf (907) and Hotel (908). Lower ID → **Golf**.

**Expected output:**

```
Golf -> DEV -> 580000.0 -> 907
```

### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(901, "Alpha", "QA", 600000),
		new Employee(902, "Bravo", "PROD", 600000),
		new Employee(903, "Charlie", "DEV", 600000),
		new Employee(904, "Delta", "DEV", 600000),
		new Employee(905, "Echo", "UI", 650000),
		new Employee(906, "Foxtrot", "QA", 580000),
		new Employee(907, "Golf", "DEV", 580000),
		new Employee(908, "Hotel", "DEV", 580000),
		new Employee(909, "India", "PROD", 580000),
		new Employee(910, "Juliett", "QA", 700000)
	);
	
	Optional<Employee> e = 
		employees.stream()
				.min(
					// rule-1: lowest salary
					Comparator.comparing(Employee::getSalary)
					// rule-2: DEV first 
					.thenComparing(emp -> emp.getDepartment().equals("DEV") ? 0 : 1)
					// rule-3: lower id
					.thenComparing(Employee::getId)
				);
	
	System.out.println(
		e.get().getName() + " -> " +
		e.get().getDepartment() + " -> " + 
		e.get().getSalary() + " -> " +
		e.get().getId()
	);
}
```

### Progression

| #  | Level         | Main concept                    |
| -- | ------------- | ------------------------------- |
| 1  | Easy          | Basic object comparison         |
| 2  | Easy          | Minimum by ID                   |
| 3  | Easy          | filter() + min()                |
| 4  | Easy/Moderate | Conditional minimum             |
| 5  | Moderate      | Minimum + tie-breaker           |
| 6  | Moderate      | groupingBy() + min()            |
| 7  | Moderate      | Filtering + different property  |
| 8  | Moderate      | Filter + minimum                |
| 9  | Advanced      | Grouping + composite comparator |
| 10 | Advanced      | Multi-level business comparator |
