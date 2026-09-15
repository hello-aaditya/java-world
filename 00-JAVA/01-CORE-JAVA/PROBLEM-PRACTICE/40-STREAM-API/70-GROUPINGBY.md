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
# `groupingBy()` Based Custom Class

### Employee class

```java
public class Employee {
	private int id;
	private String name;
	private String department;
	private String designation;
	private double salary;
	private int experience;
	
	public Employee (
		int id,
		String name,
		String department,
		String designation,
		double salary,
		int experience
	) {
		this.id = id;
		this.name = name;
		this.department = department;
		this.designation = designation;
		this.salary = salary;
		this.experience = experience;
	}
	
	public int getId() {
		return id;
	}
	
	public String getName() {
		return name;
	}
	
	public String getDepartment() {
		return department;
	}
	
	public String getDesignation() {
		return designation;
	}
	
	public double getSalary() {
		return salary;
	}
	
	public int getExperience() {
		return experience;
	}
}
```

### 1. Group Employees by Department

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(101, "Alpha",   "DEV", "Developer",         850000, 2),
    new Employee(102, "Bravo",   "QA",  "Tester",            720000, 3),
    new Employee(103, "Charlie", "DEV", "Developer",         950000, 5),
    new Employee(104, "Delta",   "HR",  "HR Executive",      680000, 4),
    new Employee(105, "Echo",    "QA",  "Automation Tester", 880000, 6),
    new Employee(106, "Foxtrot", "DEV", "Tech Lead",        1250000, 9),
    new Employee(107, "Golf",    "HR",  "HR Manager",       1050000, 8)
);
```

Group all employees by their **department** using `groupingBy()`.

**Expected output:**

```
DEV -> [Alpha, Charlie, Foxtrot]
QA -> [Bravo, Echo]
HR -> [Delta, Golf]
```

### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(101, "Alpha", "DEV", "Developer", 850000, 2),
		new Employee(102, "Bravo", "QA", "Tester", 720000, 3),
		new Employee(103, "Charlie", "DEV", "Developer", 950000, 5),
		new Employee(104, "Delta", "HR", "HR Executive", 680000, 4),
		new Employee(105, "Echo", "QA", "Automation Tester", 880000, 6),
		new Employee(106, "Foxtrot", "DEV", "Tech Lead", 1250000, 9),
		new Employee(107, "Golf", "HR", "HR Manager", 1050000, 8)
	);
	
	employees.stream()
			.collect(
				Collectors.groupingBy(e -> e.getDepartment()
				)
			)
			.forEach((dept, employeeList) -> {
				System.out.println (
					dept + " -> " +
						employeeList.stream()
								.map(e -> e.getName())
								.collect(Collectors.toList())
				);
			});
			

}
```

### 2. Group Employees by Designation

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(201, "Alpha",   "DEV", "Developer",         800000, 2),
    new Employee(202, "Bravo",   "QA",  "Tester",            700000, 2),
    new Employee(203, "Charlie", "DEV", "Developer",         900000, 4),
    new Employee(204, "Delta",   "DEV", "Tech Lead",        1250000, 8),
    new Employee(205, "Echo",    "QA",  "Tester",            760000, 3),
    new Employee(206, "Foxtrot", "HR",  "HR Executive",      650000, 3),
    new Employee(207, "Golf",    "DEV", "Developer",         870000, 3),
    new Employee(208, "Hotel",   "QA",  "Automation Tester", 950000, 6)
);
```

Group employees by their **designation** using `groupingBy()`.

**Expected output:**

```
Developer = [Alpha, Charlie, Golf]
Tester = [Bravo, Echo]
Tech Lead = [Delta]
HR Executive = [Foxtrot]
Automation Tester = [Hotel]
```

### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(201, "Alpha", "DEV", "Developer", 800000, 2),
		new Employee(202, "Bravo", "QA", "Tester", 700000, 2),
		new Employee(203, "Charlie", "DEV", "Developer", 900000, 4),
		new Employee(204, "Delta", "DEV", "Tech Lead", 1250000, 8),
		new Employee(205, "Echo", "QA", "Tester", 760000, 3),
		new Employee(206, "Foxtrot", "HR", "HR Executive", 650000, 3),
		new Employee(207, "Golf", "DEV", "Developer", 870000, 3),
		new Employee(208, "Hotel", "QA", "Automation Tester", 950000, 6)
	);
	
	employees.stream()
			.collect(
				Collectors.groupingBy(e -> e.getDesignation())
			)
			.forEach((designation, employeeList) -> {
				System.out.println(
					designation + " = " +
					employeeList.stream()
							.map(e -> e.getName())
							.collect(Collectors.toList())
				);
			});

}
```

### 3. Group Employees by Experience Level

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(301, "Alpha",   "DEV", "Developer", 700000,  1),
    new Employee(302, "Bravo",   "QA",  "Tester",    720000,  2),
    new Employee(303, "Charlie", "DEV", "Developer", 850000,  3),
    new Employee(304, "Delta",   "HR",  "Executive", 800000,  5),
    new Employee(305, "Echo",    "QA",  "Tester",    950000,  4),
    new Employee(306, "Foxtrot", "DEV", "Tech Lead", 1300000, 6),
    new Employee(307, "Golf",    "HR",  "Manager",   1200000, 8),
    new Employee(308, "Hotel",   "DEV", "Architect", 1600000, 10)
);
```

Group employees by **experience level**, calculated from the `experience` field:
- `0–2 years` → `"JUNIOR"`
- `3–5 years` → `"MID_LEVEL"`
- `6+ years`  → `"SENIOR"`

**Expected output:**

```
JUNIOR = [Alpha, Bravo]
MID_LEVEL = [Charlie, Delta, Echo]
SENIOR = [Foxtrot, Golf, Hotel]
```

### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(301, "Alpha", "DEV", "Developer", 700000, 1),
		new Employee(302, "Bravo", "QA", "Tester", 720000, 2),
		new Employee(303, "Charlie", "DEV", "Developer", 850000, 3),
		new Employee(304, "Delta", "HR", "Executive", 800000, 5),
		new Employee(305, "Echo", "QA", "Tester", 950000, 4),
		new Employee(306, "Foxtrot", "DEV", "Tech Lead", 1300000, 6),
		new Employee(307, "Golf", "HR", "Manager", 1200000, 8),
		new Employee(308, "Hotel", "DEV", "Architect", 1600000, 10)
	);

	employees.stream()
			.collect(
				Collectors.groupingBy(e -> {
					int experience = e.getExperience();
					
					if (experience <= 2) {
						return "JUNIOR";
					} else if (experience <= 5) {
						return "MID_LEVEL";
					} else {
						return "SENIOR";
					}
				})
			)
			.forEach((exp, emp) -> {
				System.out.println(
					exp + " = " +
					emp.stream()
						.map(e -> e.getName())
						.collect(Collectors.toList())
				);
			});
}
```

### 4. Group Employees by Salary Band

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(401, "Alpha",   "DEV", "Developer", 750000,  2),
    new Employee(402, "Bravo",   "QA",  "Tester",    800000,  3),
    new Employee(403, "Charlie", "DEV", "Developer", 950000,  4),
    new Employee(404, "Delta",   "HR",  "Executive", 1100000, 5),
    new Employee(405, "Echo",    "QA",  "Tester",    1199999, 6),
    new Employee(406, "Foxtrot", "DEV", "Tech Lead", 1200000, 8),
    new Employee(407, "Golf",    "HR",  "Manager",   1450000, 10),
    new Employee(408, "Hotel",   "DEV", "Architect", 1750000, 12)
);
```

Group employees by **salary band**, calculated from the `salary` field:
- `salary < 800000` → `"LOW"`
- `800000 <= salary <= 1199999` → `"MEDIUM"`
- `salary >= 1200000` → `"HIGH"`

**Expected output:**

```
LOW = [Alpha]
MEDIUM = [Bravo, Charlie, Delta, Echo]
HIGH = [Foxtrot, Golf, Hotel]
```

### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(401, "Alpha", "DEV", "Developer", 750000, 2),
		new Employee(402, "Bravo", "QA", "Tester", 800000, 3),
		new Employee(403, "Charlie", "DEV", "Developer", 950000, 4),
		new Employee(404, "Delta", "HR", "Executive", 1100000, 5),
		new Employee(405, "Echo", "QA", "Tester", 1199999, 6),
		new Employee(406, "Foxtrot", "DEV", "Tech Lead", 1200000, 8),
		new Employee(407, "Golf", "HR", "Manager", 1450000, 10),
		new Employee(408, "Hotel", "DEV", "Architect", 1750000, 12)
	);
	
	employees.stream()
			.collect(
				Collectors.groupingBy(e -> {
					double salary = e.getSalary();
					
					if (salary < 800000) {
						return "LOW";
					} else if (salary >= 800000 && salary <= 1199999) {
						return "MEDIUM";
					} else {
						return "HIGH";
					}
				})
			)
			.forEach((salary, emp) -> {
				System.out.println(
					salary + " = " +
					emp.stream()
						.map(e -> e.getName())
						.collect(Collectors.toList())
					
				);
			});

}
```

### 5. Count Employees in Each Department

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(501, "Alpha",   "DEV", "Developer",         850000, 2),
    new Employee(502, "Bravo",   "QA",  "Tester",            720000, 3),
    new Employee(503, "Charlie", "DEV", "Developer",         950000, 5),
    new Employee(504, "Delta",   "HR",  "Executive",         680000, 4),
    new Employee(505, "Echo",    "QA",  "Tester",            880000, 6),
    new Employee(506, "Foxtrot", "DEV", "Tech Lead",        1250000, 9),
    new Employee(507, "Golf",    "HR",  "Manager",          1050000, 8),
    new Employee(508, "Hotel",   "DEV", "Developer",         900000, 4),
    new Employee(509, "India",   "QA",  "Automation Tester", 980000, 7)
);
```

Group by department and use a **downstream `counting()` collector** to count employees in each. Result is `Map<String, Long>`.

**Expected output:**

```
DEV = 4
QA = 3
HR = 2
```

### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(501, "Alpha", "DEV", "Developer", 850000, 2),
		new Employee(502, "Bravo", "QA", "Tester", 720000, 3),
		new Employee(503, "Charlie", "DEV", "Developer", 950000, 5),
		new Employee(504, "Delta", "HR", "Executive", 680000, 4),
		new Employee(505, "Echo", "QA", "Tester", 880000, 6),
		new Employee(506, "Foxtrot", "DEV", "Tech Lead", 1250000, 9),
		new Employee(507, "Golf", "HR", "Manager", 1050000, 8),
		new Employee(508, "Hotel", "DEV", "Developer", 900000, 4),
		new Employee(509, "India", "QA", "Automation Tester", 980000, 7)
	);
	
	employees.stream()
			.collect(
					Collectors.groupingBy( e -> e.getDepartment(),
							Collectors.counting()
					)
			)
			.forEach((dept, countOfEmp) -> {
				System.out.println(dept + " = " + countOfEmp);
			});
}
```

### 6. Calculate Total Salary Expense by Department

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(601, "Alpha",   "DEV", "Developer", 800000,  2),
    new Employee(602, "Bravo",   "QA",  "Tester",    700000,  3),
    new Employee(603, "Charlie", "DEV", "Developer", 950000,  5),
    new Employee(604, "Delta",   "HR",  "Executive", 650000,  4),
    new Employee(605, "Echo",    "QA",  "Tester",    850000,  6),
    new Employee(606, "Foxtrot", "DEV", "Tech Lead", 1250000, 9),
    new Employee(607, "Golf",    "HR",  "Manager",   1100000, 8)
);
```

Group by department and use a **downstream `summingDouble()` collector** to calculate total salary per department.

**Expected output:**

```
DEV = 3000000.0
QA = 1550000.0
HR = 1750000.0
```

### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(601, "Alpha", "DEV", "Developer", 800000, 2),
		new Employee(602, "Bravo", "QA", "Tester", 700000, 3),
		new Employee(603, "Charlie", "DEV", "Developer", 950000, 5),
		new Employee(604, "Delta", "HR", "Executive", 650000, 4),
		new Employee(605, "Echo", "QA", "Tester", 850000, 6),
		new Employee(606, "Foxtrot", "DEV", "Tech Lead", 1250000, 9),
		new Employee(607, "Golf", "HR", "Manager", 1100000, 8)
	);
	
	employees.stream()
			.collect(
				Collectors.groupingBy(e -> e.getDepartment(),
					Collectors.summingDouble(e -> e.getSalary())
				)
			)
			.forEach((dept, totalAnnualSalary) -> {
				System.out.println(dept + " = " + totalAnnualSalary);
			});

}
```

### 7. Calculate Average Salary by Designation

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(701, "Alpha",   "DEV", "Developer",  800000, 2),
    new Employee(702, "Bravo",   "QA",  "Tester",     700000, 3),
    new Employee(703, "Charlie", "DEV", "Developer",  900000, 4),
    new Employee(704, "Delta",   "QA",  "Tester",     800000, 5),
    new Employee(705, "Echo",    "DEV", "Developer", 1000000, 6),
    new Employee(706, "Foxtrot", "DEV", "Tech Lead", 1300000, 9),
    new Employee(707, "Golf",    "QA",  "Tester",     900000, 7)
);
```

Group by designation and use a **downstream `averagingDouble()` collector** to calculate average salary per designation.

**Expected output:**

```
Developer = 900000.0
Tester = 800000.0
Tech Lead = 1300000.0
```

### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(701, "Alpha", "DEV", "Developer", 800000, 2),
		new Employee(702, "Bravo", "QA", "Tester", 700000, 3),
		new Employee(703, "Charlie", "DEV", "Developer", 900000, 4),
		new Employee(704, "Delta", "QA", "Tester", 800000, 5),
		new Employee(705, "Echo", "DEV", "Developer", 1000000, 6),
		new Employee(706, "Foxtrot", "DEV", "Tech Lead", 1300000, 9),
		new Employee(707, "Golf", "QA", "Tester", 900000, 7)
	);
	
	employees.stream()
			.collect(
				Collectors.groupingBy(e -> e.getDesignation(),
					Collectors.averagingDouble(e -> e.getSalary())
				)
			)
			.forEach((designation, avgSalary) -> {
				System.out.println(designation + " = " + avgSalary);
			});

}
```

### 8. Find the Highest-Paid Employee in Each Department

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(801, "Alpha",   "DEV", "Developer",          850000, 2),
    new Employee(802, "Bravo",   "DEV", "Developer",         1100000, 5),
    new Employee(803, "Charlie", "DEV", "Tech Lead",         1450000, 9),

    new Employee(804, "Delta",   "QA",  "Tester",             720000, 3),
    new Employee(805, "Echo",    "QA",  "Automation Tester",  950000, 6),
    new Employee(806, "Foxtrot", "QA",  "QA Lead",           1200000, 8),

    new Employee(807, "Golf",    "HR",  "Executive",          680000, 4),
    new Employee(808, "Hotel",   "HR",  "Manager",           1050000, 8)
);
```

Group by department and use a **downstream `maxBy()` collector** to find the highest-paid employee in each.

**Expected output:**

```
DEV = Charlie
QA = Foxtrot
HR = Hotel
```

### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(801, "Alpha", "DEV", "Developer", 850000, 2),
		new Employee(802, "Bravo", "DEV", "Developer", 1100000, 5),
		new Employee(803, "Charlie", "DEV", "Tech Lead", 1450000, 9),

		new Employee(804, "Delta", "QA", "Tester", 720000, 3),
		new Employee(805, "Echo", "QA", "Automation Tester", 950000, 6),
		new Employee(806, "Foxtrot", "QA", "QA Lead", 1200000, 8),

		new Employee(807, "Golf", "HR", "Executive", 680000, 4),
		new Employee(808, "Hotel", "HR", "Manager", 1050000, 8)
	);
	
	employees.stream()
			.collect(
				Collectors.groupingBy(e -> e.getDepartment(),
					Collectors.maxBy(
						Comparator.comparingDouble(e -> e.getSalary())
					)
				)
			)
			.forEach((dept, emp) -> {
				System.out.println(dept + " = " + emp.get().getName());
			});

}
```

### 9. Group Employees by Department and Then by Designation

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(901, "Alpha",   "DEV", "Developer", 800000,  2),
    new Employee(902, "Bravo",   "DEV", "Developer", 900000,  4),
    new Employee(903, "Charlie", "DEV", "Tech Lead", 1300000, 8),

    new Employee(904, "Delta",   "QA",  "Tester",    700000,  3),
    new Employee(905, "Echo",    "QA",  "Tester",    800000,  5),
    new Employee(906, "Foxtrot", "QA",  "QA Lead",   1150000, 8),

    new Employee(907, "Golf",    "HR",  "Executive", 650000,  3),
    new Employee(908, "Hotel",   "HR",  "Manager",   1050000, 7),
    new Employee(909, "India",   "HR",  "Executive", 720000,  4)
);
```

First group by **department**, then within each department further group by **designation** using nested `groupingBy()`. Result is `Map<String, Map<String, List<Employee>>>`.

**Expected output:**

```
DEV
     Developer = [Alpha, Bravo]
     Tech Lead = [Charlie]

QA
     Tester = [Delta, Echo]
     QA Lead = [Foxtrot]

HR
     Executive = [Golf, India]
     Manager = [Hotel]
```

### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(901, "Alpha", "DEV", "Developer", 800000, 2),
		new Employee(902, "Bravo", "DEV", "Developer", 900000, 4),
		new Employee(903, "Charlie", "DEV", "Tech Lead", 1300000, 8),

		new Employee(904, "Delta", "QA", "Tester", 700000, 3),
		new Employee(905, "Echo", "QA", "Tester", 800000, 5),
		new Employee(906, "Foxtrot", "QA", "QA Lead", 1150000, 8),

		new Employee(907, "Golf", "HR", "Executive", 650000, 3),
		new Employee(908, "Hotel", "HR", "Manager", 1050000, 7),
		new Employee(909, "India", "HR", "Executive", 720000, 4)
	);
	
	employees.stream()
			.collect(
				Collectors.groupingBy(e -> e.getDepartment(),
					Collectors.groupingBy(e -> e.getDesignation())
				)
			)
			.forEach((dept, desig) -> {
				System.out.println(dept);
				desig.forEach((d, listOfEmp) -> {
					System.out.println(
						" \t " + d + " = " +
							listOfEmp.stream()
									.map(e -> e.getName())
									.collect(Collectors.toList())
					);
				});
			});
	

}
```

### 10. Department Performance Summary

Given:

```java
List<Employee> employees = Arrays.asList(
    new Employee(1001, "Alpha",   "DEV", "Developer",         800000, 2),
    new Employee(1002, "Bravo",   "DEV", "Developer",         950000, 4),
    new Employee(1003, "Charlie", "DEV", "Tech Lead",        1400000, 9),

    new Employee(1004, "Delta",   "QA",  "Tester",            700000, 3),
    new Employee(1005, "Echo",    "QA",  "Automation Tester", 900000, 6),
    new Employee(1006, "Foxtrot", "QA",  "QA Lead",          1200000, 8),

    new Employee(1007, "Golf",    "HR",  "Executive",         650000, 3),
    new Employee(1008, "Hotel",   "HR",  "Manager",          1050000, 7),
    new Employee(1009, "India",   "HR",  "Executive",         750000, 5)
);
```

For every department produce a summary containing all three of the following using `groupingBy()` and downstream collectors — **employee count**, **total salary**, **highest-paid employee**. Do not create a separate custom class for the result.

**Expected output:**

```
DEV
    count = 3
    totalSalary = 3150000.0
    highestPaidEmployee = Charlie

QA
    count = 3
    totalSalary = 2800000.0
    highestPaidEmployee = Foxtrot

HR
    count = 3
    totalSalary = 2450000.0
    highestPaidEmployee = Hotel
```

### Solution
```java
```
Question-10 unsolved