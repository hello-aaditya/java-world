# File Class
Before reading from or writing to a file, it is often necessary to:
- check whether a file exists
- verify permissions
- identify whether a path refers to a file or a directory

Java provides the **`File` class** for these purposes.
### Commonly Used Methods of `File` Class
|Sl No|File Method Name|Return Type|Why Use?|
|--:|---|---|---|
|1|`exists()`|`boolean`|Checks whether the file or directory exists|
|2|`canRead()`|`boolean`|Checks if the file is readable|
|3|`canWrite()`|`boolean`|Checks if the file can be written to|
|4|`canExecute()`|`boolean`|Checks if the file is executable|
|5|`isFile()`|`boolean`|Confirms whether the path refers to a file|
|6|`isDirectory()`|`boolean`|Confirms whether the path refers to a directory|
|7|`getName()`|`String`|Returns the name of the file or directory|
|8|`getPath()`|`String`|Returns the path used to create the `File` object|
|9|`getAbsolutePath()`|`String`|Returns the complete absolute file path|
|10|`length()`|`long`|Returns the size of the file in bytes|
|11|`mkdir()`|`boolean`|Creates a single directory|
|12|`mkdirs()`|`boolean`|Creates directory along with parent directories|
|13|`delete()`|`boolean`|Deletes the file or directory|
|14|`list()`|`String[]`|Lists names of files/directories inside a directory|
|15|`listFiles()`|`File[]`|Lists files/directories as `File` objects|
```java
package advanced_java.fileHandling;

import java.io.File;

public class FileMethods {

	public static void main(String[] args) {
		
		String inputPath ="/home/mcclusky/fileHandling/input.txt";
		
		File file = new File(inputPath);
		
		System.out.println(file.canRead());
		System.out.println(file.canWrite());
		System.out.println(file.canExecute());
		
		System.out.println(file.getAbsolutePath());
		
		System.out.println(file.isFile());
		System.out.println(file.isDirectory());
	}

}
```