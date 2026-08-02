# Copying Files
Read data from a source file and write the same into another file.
## 8.1) Example (Copy File Using `FileInputStream` and `FileOutputStream`):
```java
package advanced_java.fileHandling;

import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class CopyTheContent {

    public static void main(String[] args) throws IOException {

        String sourceFilePath = "/home/mcclusky/fileHandling/input.txt";
        String destinationFilePath = "/home/mcclusky/fileHandling/output.txt";

        FileInputStream inputFileStream = new FileInputStream(sourceFilePath);
        FileOutputStream outputFileStream = new FileOutputStream(destinationFilePath);

        int byteData;
        while ((byteData = inputFileStream.read()) != -1) {
            outputFileStream.write(byteData);
        }

        System.out.println("File copy completed.");

        inputFileStream.close();
        outputFileStream.close();
    }
}
```
> This approach copies a file **byte by byte**, making it suitable for both text and binary files.

#### 8.2) Copying Text Files Using `BufferedReader` and `BufferedWriter`
In the previous example, we copied a file **byte by byte** using byte streams.  
That approach works for **all types of files**, but it is **not the best choice for text files**.

Text files contain **human-readable characters**, so Java provides a **character-based and more convenient way** to copy them.
##### When working with text files:
- We usually read **line by line**
- We want Java to handle **character encoding**
- We want **better performance** and **cleaner code**

`BufferedReader` and `BufferedWriter` are designed exactly for this purpose.

> For text files, character streams with buffering are preferred over byte streams.
#### How Text File Copying Works (Conceptual)
When copying a text file using buffered character streams:
1. The program opens the source text file using `BufferedReader`
2. It reads the file **one line at a time**
3. Each line is written to the destination file using `BufferedWriter`
4. This process continues until the end of the file is reached
5. All resources are closed after the operation
#### Example: Copy Text File Using `BufferedReader` and `BufferedWriter`
```java
package advanced_java.fileHandling;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

public class CopyTextFileUsingBufferedStreams {

    public static void main(String[] args) throws IOException {

        String sourceFilePath = "/home/mcclusky/fileHandling/input.txt";
        String destinationFilePath = "/home/mcclusky/fileHandling/output.txt";

        BufferedReader bufferedReader =
                new BufferedReader(new FileReader(sourceFilePath));

        BufferedWriter bufferedWriter =
                new BufferedWriter(new FileWriter(destinationFilePath));

        String lineData;
        while ((lineData = bufferedReader.readLine()) != null) {
            bufferedWriter.write(lineData);
            bufferedWriter.newLine();   // preserve line breaks
        }

        System.out.println("Text file copy completed.");

        bufferedReader.close();
        bufferedWriter.close();
    }
}
```
**Conclusion:**
##### 1. Reading Line by Line
```java
bufferedReader.readLine()
```
- Reads one full line of text
- Returns `null` when the end of the file is reached
##### 2. Writing Text Properly
```java
bufferedWriter.write(lineData);
bufferedWriter.newLine();
```
- Writes the line content
- Adds a new line so the file structure remains unchanged

Without `newLine()`, all lines would merge into one.
## 8.3) Copying Files Using Buffered Byte Streams
In the earlier examples:
- we copied files using **basic byte streams**
- and copied text files using **buffered character streams**

Now we’ll see how to **improve byte-based copying** using **buffered byte streams**.

This approach is mainly used for **binary files** and **large files**.
### Example: Copy File Using `BufferedInputStream` and `BufferedOutputStream`
```java
package advanced_java.fileHandling;

import java.io.BufferedInputStream;
import java.io.BufferedOutputStream;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class CopyFileUsingBufferedByteStreams {

    public static void main(String[] args) throws IOException {

        String sourceFilePath = "/home/mcclusky/fileHandling/input.txt";
        String destinationFilePath = "/home/mcclusky/fileHandling/output.txt";

        BufferedInputStream bufferedInputStream =
                new BufferedInputStream(new FileInputStream(sourceFilePath));

        BufferedOutputStream bufferedOutputStream =
                new BufferedOutputStream(new FileOutputStream(destinationFilePath));

        int byteData;
        while ((byteData = bufferedInputStream.read()) != -1) {
            bufferedOutputStream.write(byteData);
        }

        System.out.println("File copy completed using buffered byte streams.");

        bufferedInputStream.close();
        bufferedOutputStream.close();
    }
}
```