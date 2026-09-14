# `max()` Based Questions
### 1 Maximum Number
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		45, 12, 89, 34, 67, 23, 91, 56
	);
	
	int maxNumber = numbers.stream()
			.max(Integer::compareTo).get();

	System.out.println(maxNumber);
}
```
### 2 Maximum Even Number
### Solution
```java
public static void main(String[] args) {
		
	List<Integer> numbers = Arrays.asList(
		17, 42, 83, 64, 91, 28, 76, 55
	);
	
	int maxEvenNumber = numbers.stream()
			.filter(n -> (n & 1) == 0)
			.max(Integer::compare)
			.get();
	
	System.out.println(maxEvenNumber);
}
```
### 3 Maximum Number Greater Than 50
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		15, 42, 87, 64, 93, 28, 76, 51, 99, 36
	);
	
	int result = numbers.stream()
			.filter(n -> (n > 50) && ((n&1) == 0)) 
			.max(Comparator.naturalOrder())
			.get();
	
	System.out.println(result);
}
```
### 4 Maximum Unique Number
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		45, 78, 23, 78, 91, 45, 67, 91, 34, 89
	);

	int result = numbers.stream()
			.distinct()
			.max(Integer::compareTo).get();
	
	System.out.println(result);
}
```
### 5 Lexicographically Maximum String
### Solution
```java
public static void main(String[] args) {
	
	List<String> names = Arrays.asList(
		"Alpha", "Charlie", "Bravo", "Delta", "Echo", "Frankie"
	);
	
	String result = names.stream()
			.max(String::compareTo).get();
	
	System.out.println(result);
}
```
### 6 Longest String
### Solution
```java
public static void main(String[] args) {
	
	List<String> keywords = Arrays.asList(
		"Java", "Stream", "Collection", "Lambda", "Programming", "API"
	);
	
	String result = keywords.stream()
			.max(Comparator.comparingInt(String::length)).get();
	
	System.out.println(result);

}
```
### 7 Longest String With Tie-Breaking
### Solution
```java
public static void main(String[] args) {
	
	List<String> words = Arrays.asList(
		"Java", "Spring", "Docker", "Python", "Lambda", "Oracle"
	);
	
	String result = 
			words.stream()
			.max(Comparator.comparingInt(String::length)
					.thenComparing(Comparator.naturalOrder())
			)
			.orElse(null);

	System.out.println(result);
}
```
### 8 Maximum Number by Absolute Value
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		-45, 12, -89, 34, 67, -23, 56, -91
	);
	
	int result = numbers.stream()
			.max(
				Comparator.comparingInt(Math::abs)
			)
			.orElseThrow();
	
	
	System.out.println(result);
}
```
### 9 Maximum Even Number Greater Than 50
### Solution
```java
public static void main(String[] args) {
	
	List<Integer> numbers = Arrays.asList(
		15, 42, 87, 64, 93, 28, 76, 51, 99, 36
	);
	
	int result = numbers.stream()
			.filter(n -> (n > 50) && ((n&1) == 0)) 
			.max(Comparator.naturalOrder())
			.get();
	
	System.out.println(result);
}
```
### 10 Maximum String Using Composite Rules
### Solution
```java
public static void main(String[] args) {

	List<String> words = Arrays.asList(
		"Java", "Spring", "Docker", "Lambda", "Kubernetes", 
		"Stream", "Database", "Microservices", "Orchestration"
	);
	
	String result = words.stream()
			.max(
				Comparator.comparing(String::length)
				.thenComparing(Comparator.naturalOrder())
			).get();
	
	System.out.println(result);

}
```
# `max()` Based Custom Class Questions
### 1 Highest Salary
### Solution
```java
public static void main(String[] args) {
		
	List<Employee> employees = Arrays.asList(
		new Employee(1011, "Alpha",   "DEV",  850000),
		new Employee(1012, "Bravo",   "QA",  920000),
		new Employee(1013, "Charlie", "PROD", 780000),
		new Employee(1014, "Delta",   "DEV", 1250000),
		new Employee(1015, "Echo",    "UI",  1050000),
		new Employee(1016, "Foxtrot", "QA",  980000),
		new Employee(1017, "Golf",    "PROD", 1150000)
	);
	
	Employee e = employees.stream()
			.max(Comparator.comparing(Employee::getSalary))
			.get();
	
	System.out.println(e.getName() + " -> " + e.getSalary());

}
```
### 2 Highest Employee ID
### Solution
```java
public static void main(String[] args) {
		
	List<Employee> employees = Arrays.asList(
		new Employee(2031, "Alpha",   "DEV",  1100000),
		new Employee(2017, "Bravo",   "QA",   1350000),
		new Employee(2045, "Charlie", "PROD",  900000),
		new Employee(2022, "Delta",   "UI",   1200000),
		new Employee(2051, "Echo",    "DEV",  1050000),
		new Employee(2038, "Foxtrot", "QA",   980000),
		new Employee(2042, "Golf",    "PROD", 1250000)
	);
	
	Employee emp = employees.stream()
			.max(Comparator.comparing(Employee::getId))
			.get();
	
	System.out.println("ID: " + emp.getId() + " -> " + emp.getName());

}
```
### 3 Highest Salary Among DEV Employees
### Solution
```java
public static void main(String[] args) {
		
	List<Employee> employees = Arrays.asList(
		new Employee(3011, "Alpha",   "QA",   1400000),
		new Employee(3012, "Bravo",   "DEV",   950000),
		new Employee(3013, "Charlie", "PROD", 1250000),
		new Employee(3014, "Delta",   "DEV",  1450000),
		new Employee(3015, "Echo",    "UI",   1600000),
		new Employee(3016, "Foxtrot", "DEV",  1350000),
		new Employee(3017, "Golf",    "QA",   1100000),
		new Employee(3018, "Hotel",   "DEV",  1280000)
	);
	
	Employee emp = 
			employees.stream()
			.filter(e -> e.getDepartment().equals("DEV"))
			.max(Comparator.comparing(Employee::getSalary))
			.get();

	System.out.println(emp.getName() + " -> " + emp.getSalary());
}
```
### 4 Highest Paid Employee in Each Department
### Solution
```java
	public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(4011, "Alpha",   "DEV",  1000000),
		new Employee(4012, "Bravo",   "DEV",  1450000),
		new Employee(4013, "Charlie", "DEV",  1250000),

		new Employee(4014, "Delta",   "QA",   900000),
		new Employee(4015, "Echo",    "QA",   1350000),
		new Employee(4016, "Foxtrot", "QA",   1150000),

		new Employee(4017, "Golf",    "PROD", 1500000),
		new Employee(4018, "Hotel",   "PROD", 1300000),
		new Employee(4019, "India",   "PROD", 1420000),

		new Employee(4020, "Juliett", "UI",   850000),
		new Employee(4021, "Kilo",    "UI",   1050000),
		new Employee(4022, "Lima",    "UI",   980000)
	);
	
	Map<String, Optional<Employee>> output = 
			employees.stream()
			.collect(
				Collectors.groupingBy(
					Employee::getDepartment,
					Collectors.maxBy(
						Comparator.comparingDouble(Employee::getSalary)
					)
				)
			);
	
	output.forEach((dept, emp) -> 
		emp.ifPresent(e -> 
			System.out.println(dept + " -> " + e.getName()))
	);

}
```
### 5 Highest Salary After Removing Duplicate Employees
### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(5011, "Alpha",   "DEV",  950000),
		new Employee(5012, "Bravo",   "QA",  1100000),
		new Employee(5013, "Charlie", "PROD", 1250000),
		new Employee(5012, "Bravo",   "QA",  1100000),  // duplicate
		new Employee(5014, "Delta",   "DEV",  1450000),
		new Employee(5015, "Echo",    "UI",  1350000),
		new Employee(5013, "Charlie", "PROD", 1250000),  // duplicate
		new Employee(5016, "Foxtrot", "QA",  1050000),
		new Employee(5017, "Golf",    "PROD", 1400000)
	);
	
	Optional<Employee> output = 
			employees.stream()
			.distinct()
			.max(Comparator.comparing(Employee::getSalary));
			
	output.ifPresent(e -> {
		System.out.println(e.getName() + " -> " + e.getSalary());
	});

}
```
### 6 Highest Salary With ID Tie-Breaking
### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(6015, "Alpha",   "DEV",  1200000),
		new Employee(6008, "Bravo",   "QA",   1450000),
		new Employee(6012, "Charlie", "PROD", 1600000),
		new Employee(6005, "Delta",   "DEV",  1600000),
		new Employee(6018, "Echo",    "UI",   1600000),
		new Employee(6009, "Foxtrot", "QA",  1350000),
		new Employee(6021, "Golf",    "PROD", 1500000)
	);
	
	Employee emp = 
	employees.stream()
			.max(
				Comparator.comparingDouble(Employee::getSalary)
					.thenComparing(
						Employee::getId,
						Comparator.reverseOrder()
					)
			)
			.get();

	System.out.println(emp);
	
}
```
### 7 Highest-Paid Employee Above Department Average
### Solution
```java
public static void main(String[] args) {

	List<Employee> employees = Arrays.asList(
		new Employee(7011, "Alpha",   "DEV",  800000),
		new Employee(7012, "Bravo",   "DEV", 1200000),
		new Employee(7013, "Charlie", "DEV", 1600000),
		new Employee(7014, "Delta",   "DEV", 1000000),

		new Employee(7015, "Echo",    "QA",   700000),
		new Employee(7016, "Foxtrot", "QA",  1100000),
		new Employee(7017, "Golf",    "QA",   900000),

		new Employee(7018, "Hotel",   "PROD", 1300000),
		new Employee(7019, "India",   "PROD", 1700000),
		new Employee(7020, "Juliett", "PROD", 1500000),

		new Employee(7021, "Kilo",    "UI",   600000),
		new Employee(7022, "Lima",    "UI",   800000),
		new Employee(7023, "Mike",    "UI",   1000000)
	);
	
	Map<String, Optional<Employee>> result = 
	employees.stream()
			.collect(
				Collectors.groupingBy(
					Employee::getDepartment,
					Collectors.maxBy(
						Comparator.comparing(Employee::getSalary)
							.thenComparing(Employee::getId)
					)
				)
			);
	
	result.forEach((dept, emp) -> {
		System.out.println("\"" + dept + "\" -> " + emp.get().getName());
	});
	
}
```
### 8 Maximum Salary Difference Between Two Employees
### Solution
```java
public static void main(String[] args) {
	
	List<Employee> employees = Arrays.asList(
		new Employee(8011, "Alpha",   "DEV",   850000),
		new Employee(8012, "Bravo",   "QA",   1250000),
		new Employee(8013, "Charlie", "PROD",  700000),
		new Employee(8014, "Delta",   "DEV",  1600000),
		new Employee(8015, "Echo",    "UI",   1050000),
		new Employee(8016, "Foxtrot", "QA",   1350000),
		new Employee(8017, "Golf",    "PROD",  950000),
		new Employee(8018, "Hotel",   "UI",    800000)
	);
	
	Employee empWithHighestSalary = 
			employees.stream()
				.max(Comparator.comparing(Employee::getSalary))
				.get();
	
	Employee empWithMinimumSalary = 
			employees.stream()
				.min(Comparator.comparing(Employee::getSalary))
				.get();
	
	double salaryDifference = 
			empWithHighestSalary.getSalary() - empWithMinimumSalary.getSalary();
	
	System.out.println(salaryDifference);
}
```
### 9 Highest-Paid Employee Per Department After Deduplication
### Solution
```java
	public static void main(String[] args) {

		List<Employee> employees = Arrays.asList(

		    new Employee(9011, "Alpha",   "DEV",  1000000),
		    new Employee(9011, "Alpha",   "DEV",  1000000), // duplicate ID

		    new Employee(9012, "Bravo",   "DEV",  1500000),
		    new Employee(9013, "Charlie", "DEV",  1500000),

		    new Employee(9014, "Delta",   "QA",   900000),
		    new Employee(9014, "Delta",   "QA",   900000),  // duplicate ID

		    new Employee(9015, "Echo",    "QA",   1300000),
		    new Employee(9016, "Foxtrot", "QA",   1300000),

		    new Employee(9017, "Golf",    "PROD", 1400000),
		    new Employee(9018, "Hotel",   "PROD", 1250000),
		    new Employee(9019, "India",   "PROD", 1350000),

		    new Employee(9020, "Juliett", "UI",   950000),
		    new Employee(9021, "Kilo",    "UI",   1100000),
		    new Employee(9021, "Kilo",    "UI",   1100000)  // duplicate ID
		);
		
		Map<String, Optional<Employee>> result = 
			employees.stream()
					.distinct()
					.collect(
						Collectors.groupingBy(
							Employee::getDepartment,
							Collectors.maxBy(
								Comparator.comparing(Employee::getSalary)
									.thenComparing(Employee::getId)
							)
						)
					);
		
		result.forEach((dept, emp) -> {
			System.out.println("\"" + dept + "\"" + " -> " + emp.get().getName());
		});
				
	}
```
### 10 Highest Salary Employee Using Composite Business Rules
### Solution
```java
```
