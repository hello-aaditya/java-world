In Java, files are handled using **streams**.  
But **not all streams work the same way**, because **not all files contain the same type of data**.

So Java provides **two main types of streams**, based on **how data is handled**
## Why Are There Different Types of Streams?
Before choosing a stream, we must understand **what kind of data a file contains**.
- Some files contain **text** that humans can read
- Some files contain **raw data** that is meant only for programs

Because of this difference, Java separates streams into:
1. **Byte Streams**
2. **Character Streams**
### 1) Byte Streams
> **Byte streams** handle data in the form of **bytes (8-bit values)**.

These streams do not try to understand characters or text.  
They simply read and write **raw bytes**.
#### When to Use Byte Streams
Use byte streams when working with **binary or non-text files**, such as:
- Images
- Audio files
- Video files
- PDF files
- Executable or software files

In such files, data is **not meant to be read as characters**.
#### Core Byte Stream Classes
- `InputStream` → for reading data
- `OutputStream` → for writing data

**Common implementations:**
- `FileInputStream`
- `FileOutputStream`
### 2) Character Streams
> **Character streams** handle data in the form of **characters**.

These streams are designed specifically for **text-based data**.
#### When to Use Character Streams
Use character streams when working with **human-readable text files**, such as:
- `.txt`
- `.log`
- `.java`
- `.csv`
- `.xml`
- `.json`

These files contain **letters, numbers, and symbols**.
#### Core Character Stream Classes
- `Reader` → for reading characters
- `Writer` → for writing characters

**Common implementations:**
- `FileReader`
- `FileWriter`

| #   | Aspect               | Byte-Based                                                    | Character-Based                      |
| --- | -------------------- | ------------------------------------------------------------- | ------------------------------------ |
| 1.  | **Data handled**     | Bytes (0s and 1s)                                             | Characters (text)                    |
| 2.  | **File type**        | Binary files                                                  | Text files                           |
| 2.  | **Java Classes**     | `InputStream`, `OutputStream`                                 | `Reader`, `Writer`                   |
| 3.  | **Used For**         | images, audio, video, PDFs, Executable or Software files etc. | `.log`, `.txt`, `.java`, `.csv` etc. |
| 4.  | **Handles Encoding** | No                                                            | Yes                                  |
| 5.  | **Example Classes**  | `FileInputStream`, `FileOutputStream`                         | `FileReader`, `FileWriter`           |
