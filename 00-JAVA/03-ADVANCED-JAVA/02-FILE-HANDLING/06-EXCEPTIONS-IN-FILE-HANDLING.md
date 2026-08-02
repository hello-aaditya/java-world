# Exception Handling in File Handling
While working with files, many things can go wrong:
- the file may not exist
- the path may be incorrect
- the program may not have permission
- an error may occur while reading or writing data

To handle such situations safely, Java uses **exception handling**.

| #   | **Exception Name**             | **Occurrence Cause**                        | **Example**                             |
| --- | ------------------------------ | ------------------------------------------- | --------------------------------------- |
| 1   | `FileNotFoundException`        | File does not exist or incorrect file path  | `new FileInputStream("abc.txt");`       |
| 2   | `IOException`                  | General I/O failure during read/write/close | `reader.read();`                        |
| 3   | `EOFException`                 | Reading beyond the end of file              | `objectInputStream.readObject();`       |
| 4   | `SecurityException`            | Access denied due to security restrictions  | Reading file without permission         |
| 5   | `UnsupportedEncodingException` | Unsupported or invalid character encoding   | `getBytes("XYZ");`                      |
| 6   | `NullPointerException`         | Stream or file reference is null            | `reader.close();` when `reader == null` |
| 7   | `IllegalArgumentException`     | Invalid argument passed to file method      | Invalid file path or buffer size        |

[Example: Try **WITHOUT** Resources (Traditional Way)](./07-RESOURCE-MANAGEMENT.md#try-without-resources-traditional-way)
[Example: Try **WITH** Resources (Automatic Resource Management)](./07-RESOURCE-MANAGEMENT.md#try-with-automatic-resource-management)

