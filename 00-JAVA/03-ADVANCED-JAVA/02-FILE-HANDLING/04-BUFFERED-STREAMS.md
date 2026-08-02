# What is Buffering
> **Buffering** means temporarily storing data in memory before reading from or writing to a file.

**Instead of:**
- reading or writing **one byte or one character at a time**

**Java can:**
- read or write **a group of data at once**

This reduces the number of direct file access operations.

# Buffered Byte Streams
Buffered byte streams work with **raw binary data** and use buffering internally.

**Common classes:**
- `BufferedInputStream`
- `BufferedOutputStream`

**They are used together with:**
- `FileInputStream`
- `FileOutputStream`
# Buffered Character Streams
Buffered character streams work with **text data** and are widely used for text files.

**Common classes:**
- `BufferedReader`
- `BufferedWriter`

**They are used together with:**
- `FileReader`
- `FileWriter`
## Why `BufferedReader` and `BufferedWriter` Are Preferred for Text
Buffered character streams provide:

- better performance
- support for reading and writing **lines of text**
- simpler and cleaner code

For example:
- `BufferedReader` provides `readLine()`
- `BufferedWriter` provides `newLine()`
## When Should You Use Buffered Streams?
Use buffered streams when:
- working with large files
- reading or writing data frequently
- handling text files line by line

**In practice:**

> **Buffered streams are preferred in most real-world applications.**