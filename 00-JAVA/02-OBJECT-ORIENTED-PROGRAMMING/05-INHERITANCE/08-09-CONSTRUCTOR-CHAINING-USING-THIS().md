# Constructor Chaining using `this()`
> **`this()`** is a special keyword in Java used to **call another constructor of the same class**.
#### Class
```java
class Demo {
	Demo() {
		this(10);
		System.out.println("Inside zero parameterized constructor");
	}
	Demo(int num1) {
		this(20, 30);
		System.out.println("Inside one parameterized constructor");
	}
	Demo(int num1, int num2) {
		System.out.println("Inside two parameterized constructor");
	}
}
``` 
#### Main Class
```java
class Main {
	public static void main(String[] args) {
		Demo d = new Demo();
	}
}
```
#### Output:
```markdown
Inside two parameterized constructor
Inside one parameterized constructor
Inside zero parameterized constructor
```
### Explanation of Control Flow
1. **Control** enters the `main()` method and finds the line
    ```java
    Demo d = new Demo();
    ```
    
    → This means the **zero-parameter constructor** of `Demo` will be executed first.
    
2. Inside the **zero-parameter constructor**, the **first line** is:
    ```java
    this(10);
    ```
    
    So, the **control immediately goes** to the **one-parameter constructor** of the same class.
    
3. Inside the **one-parameter constructor**, the **first line** is again:
    ```java
    this(20, 30);
    ```
    
    So now, the **control goes** to the **two-parameter constructor**.
    
4. The **two-parameter constructor** executes first and prints:
    ```java
    Inside two parameterized constructor
    ```
    
    Once it finishes, the **control comes back** to where it was called —  
    that is, to the **one-parameter constructor**.
    
5. Now, the **one-parameter constructor** executes its next line:
    ```java
    Inside one parameterized constructor
    ```
    
    and the **control comes back** again to the **zero-parameter constructor**.
    
6. Finally, the **zero-parameter constructor** executes its last line:
    ```java
    Inside zero parameterized constructor
    ```
    

So, the order of execution becomes:

`Two-parameter constructor ↓ One-parameter constructor ↓ Zero-parameter constructor`
```markdown
Two-parameter constructor
↓
One-parameter constructor
↓
Zero-parameter constructor
```

### Conditions to Use `this()`

1. `this()` must always be **the first line** inside a constructor.  
    You cannot write anything (not even a print statement) before it.
    
2. You can use either `this()` or `super()` inside a constructor, **but not both together**.
    
3. `this()` is used to call **another constructor within the same class**,  
    while `super()` is used to call **the parent class constructor**.
### Difference Between `this()` and `super()`
|Keyword|Used For|Calls Constructor From|Must Be First Statement?|Allowed Together?|
|---|---|---|---|---|
|`this()`|Constructor chaining _within same class_|Same class|Yes|❌ No|
|`super()`|Constructor chaining _between parent and child classes_|Parent class|Yes|❌ No|
