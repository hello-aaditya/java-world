When a Java program works with files, it uses **resources** such as:
- file streams
- readers
- writers
- buffers

These resources use **system memory and file locks**, so they **must be released** after use.

Releasing resources is called **resource management**.

## 1. Closing Resources Manually (Traditional Way)
Before Java 7, resources were closed **manually** using `try-catch-finally`.

**Basic Idea**
- Open file resources inside the `try` block
- Handle exceptions in the `catch` block
- Close resources in the `finally` block

> The `finally` block always executes, whether an exception occurs or not.

### Why `finally` Is Used for Closing Files
Because:
- file operations may fail
- exceptions may occur before the program finishes
- we still want to close the file in all cases

So, `finally` ensures that resource cleanup **always happens**.
## 2. Try-With-Resources (Recommended Way)
Java 7 introduced **try-with-resources** to simplify resource management.

> Try-with-resources automatically closes resources when the `try` block ends.

### How Try-With-Resources Works (Conceptual)
- Resources are declared inside the `try` parentheses
- Java automatically closes them
- Resources are closed even if an exception occurs

This removes the need for:
- explicit `close()` calls
- `finally` blocks for resource cleanup
# 1) Try **WITHOUT** Resources (Traditional way)
#### Example: Reading a file (manual close required)
```java
import java.io.FileInputStream;

public class TryWithoutResourcesExample {

    public static void main(String[] args) {

        FileInputStream fileInputStream = null;

        try {
            fileInputStream = new FileInputStream("input.txt");

            int byteData;
            while ((byteData = fileInputStream.read()) != -1) {
                System.out.print((char) byteData);
            }

        } catch (Exception exception) {
            exception.printStackTrace();
        } finally {
            try {
                if (fileInputStream != null) {
                    fileInputStream.close();   // manual closing
                }
            } catch (Exception exception) {
                exception.printStackTrace();
            }
        }
    }
}
```
# 2) Try **WITH** Resources (Automatic Resource Management)
#### Example: Read a file and display its content
```java
import java.io.FileInputStream;

public class TryWithResourcesExample {

    public static void main(String[] args) {

        try (FileInputStream fileInputStream = new FileInputStream("input.txt")) {

            int byteData;
            while ((byteData = fileInputStream.read()) != -1) {
                System.out.print((char) byteData);
            }

        } catch (Exception exception) {
            exception.printStackTrace();
        }
    }
}
```

