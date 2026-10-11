# 1. Introduction
- In Java, to take input from the user, we use the `Scanner class`.
- Scanner is part of the `java.util` package.
- To use it, we must import:
	```JAVA
	import java.util.Scanner;	
	```
# 2. Creating Scanner Object
- Syntax:
	```JAVA
	Scanner input = new Scanner(System.in);
	```
- Here:
	- `input` → object name (can be anything).
	- `System.in` → standard input stream (keyboard).
# 3. Common Scanner Methods

![Take User Input](Take_User_Input.drawio.svg)
# 4. String Input Example
## 4.1 Take a Single Word (`scanner.next()`)
- Reads input until the first space.
- If you type `Ajay Kumar`, it will only take `Ajay`.
	```JAVA
	Scanner input = new Scanner(System.in);
	System.out.print("Enter your first name: ");
	String firstName = input.next();  
	System.out.println("Hello, " + firstName);
	```
## 4.2 Take a Whole Line (`scanner.nextLine()`)
- Reads the entire line, including spaces.
- If you type `Ajay Kumar`, it will take `Ajay Kumar`.
	```JAVA
	Scanner input = new Scanner(System.in);
	System.out.print("Enter your full name: ");
	String fullName = input.nextLine();  
	System.out.println("Hello, " + fullName);
	```
## 4.3 Take a Single Character (`scanner.next().charAt(0)`)
- Reads one word with `next()`, then picks only the **first character**.
- Useful when you want a single character input like gender (`M`/`F`) or grade (`A`, `B`, etc.).
	```JAVA
	Scanner input = new Scanner(System.in);
	System.out.print("Enter your gender (M/F): ");
	char gender = input.next().charAt(0);  
	System.out.println("Gender: " + gender);
	```
# 5. Closing Scanner
- Always close scanner at the end to release resources:
	```JAVA
	input.close();
	```
## 5.1 Why Closing Scanner?
### i. Scanner Uses System Resources
- When you create:
	```JAVA
	Scanner input = new Scanner(System.in);
	```
- It opens a connection to the **input stream** (your keyboard).
    - This connection uses **system resources (memory + I/O handle)**.
If you don’t close it → the resources stay occupied until the program ends.  
In short: **it’s like leaving a tap running** 💧.
### ii. Best Practice
- In real-world coding (big projects), programs may open many files, sockets, databases, etc.
- Not closing them can cause **memory leaks** or “too many open resources” error.
- That’s why Java recommends closing any stream/reader (Scanner, FileReader, etc.) when done.
	```JAVA
	input.close();
	```
### iii. Special Case: System.in
⚠️ But with `System.in` (keyboard input):
- Once you close the Scanner, you can’t use it again in the same program → input is gone.
- Example:
	```JAVA
	input.close();
	// Later trying new Scanner(System.in) may throw exception
	```
- So usually, we **close Scanner only at the very end of the program** (last line).
# 6. Scanner Input, Buffer Issues, and Consuming `\n`
## Example 1: Name, Age, and Area
Code:
```JAVA
import java.util.Scanner;

public class InputExample1 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter your name: ");
        String name = input.nextLine();   // full string input
        System.out.println("Your name is: " + name);

        System.out.print("Enter your age: ");
        int age = input.nextInt();        // reads only number
        sc.nextLine();                 // consume leftover '\n'
        System.out.println("Your age is: " + age);

        System.out.print("Enter your area: ");
        String area = input.nextLine();   // now works fine
        System.out.println("Your area is: " + area);

        input.close();
    }
}

```
### Explanation

1. When we type age (e.g., `20⏎`), buffer has:
	```text
	[ '2' ][ '0' ][ '\n' ]
	```
2. `nextInt()` drinks `20` but leaves `\n`.  
	Buffer now:
	```text
	[ '\n' ]
	```
3. **`input.nextLine()`** (the extra one) removes that `\n`.  
    Buffer becomes empty.
4. Now the next `nextLine()` for **area** works properly.

👉 Without the extra `input.nextLine()`, the **area input will be skipped**.

## Example 2: Roll Number and Full Name
**Code**
```JAVA
import java.util.Scanner;

public class InputExample2 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter your roll number: ");
        int roll = input.nextInt();      // reads number only
        input.nextLine();                // consume leftover '\n'

        System.out.print("Enter your full name: ");
        String fullName = input.nextLine();  // now reads correctly

        System.out.println("Roll: " + roll);
        System.out.println("Name: " + fullName);

        input.close();
    }
}

```
### Explanation

1. If user types:
	```text
	101⏎
	```
2. Buffer is:
	```Text
	[ '1' ][ '0' ][ '1' ][ '\n' ]
	```
3. Extra `input.nextLine()` removes the leftover `\n`.  
    Buffer becomes empty.
4. Now `nextLine()` for **name** waits and properly reads `"John Doe⏎"`.

👉 Without the extra `input.nextLine()`, the name input would come out **empty ("")**.

[**PTO**](150-METHOD.md)