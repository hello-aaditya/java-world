# Constructor And Static Block Execution Order
```java
public class Program {
	Program() {
	System.out.println("Constructor Executed");
	}
	
	static {
	System.out.println("Static Block Executed);
	}
	
	{
		System.out.println("Non-Static Block Executed");
	}
}
```

```java
public class Main {
	public static void main(String[] args) {
		Program p1 = new Program();
		System.out.println();
		Program p2 = new Program();
	}
}
```

#### Output:
```output
Static Block Executed
Non-Static Block Executed
Constructor Executed

Non-Static Block Executed
Constructor Executed
```

### Explanation
##### 1. Program loading phase
Before `main()` starts running, the **JVM loads the class `Program`** into memory.

While loading a class, **static blocks** get the **first priority** because they are executed **only once** — when the class is loaded for the first time.

So before creating any object,  
the control first executes the **static block**:
```java
Static Block Executed
```
Static blocks are used when we want to **initialize static data** or run setup code before any object is created.
##### 2. Object creation — `Program p1 = new Program();`
Now, the control moves to the line where the first object `p1` is created.

Object creation in Java happens in this order:

1. **Memory allocation** for the object in heap.
    
2. **Non-static (instance) block** executes — it runs _every time_ a new object is created.
    
3. **Constructor** executes — it runs _after_ the instance block, to complete the object creation.
    

So, during the creation of `p1`, the order is:
```output
Non-Static Block Executed
Constructor Executed
```
##### 3. Blank line in output
We have a `System.out.println();` in `main()`, so it just prints a blank line.
##### 4. Second object — `Program p2 = new Program();`
Now, class `Program` is **already loaded**,  
so the **static block won’t execute again**.  
It runs only once per class loading.

For this new object (`p2`), the order again is:
```output
Non-Static Block Executed
Constructor Executed
```
