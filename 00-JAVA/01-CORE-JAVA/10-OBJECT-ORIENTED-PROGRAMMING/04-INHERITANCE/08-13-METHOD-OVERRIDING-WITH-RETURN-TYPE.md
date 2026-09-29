# Method Overriding with Return Types
> “In method overriding, the return type of the overridden method in the child class must be the same as the parent class.”

### Example:
#### Parent Class
```java
public class Program1 {
	void display() {
		System.out.println("Inside Program1 Display Method");
	}
}
```
#### Child Class
```java
public class Program2 extends Program1 {
	@Override
	void display() {
		System.out.println("Inside Program2 Display Method");
	}
}
```

#### Main Class
```java
public class Main {
	public static void main(String[] args) {
		Program2 p2 = new Program2();
		p2.display();
	}
}
```
#### Output
```markdown
Inside Program2 Display Method
```

---
# Covariant Return Type
![Covariant Return Type](covariantReturnType.png)
