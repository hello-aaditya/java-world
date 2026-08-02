# What is a File?
> A **file** is a named location on a storage device used to store data permanently.

**Examples of files:**
- **Text files** (`.txt`, `.log`, `.java`)
- **Media files** (`.jpg`, `.mp3`, `.mp4`)
- **Documents** (`.pdf`, `.csv`)

Files can be categorized into two types depending on the data stored inside them:
1) Text Files
2) Binary Files
### 1) Text Files
> **Text files** store data in the form of **readable characters** (letters, numbers, symbols).

**Characteristics:**
- Human-readable
- Can be opened in a text editor
- Data is stored as characters
    
**Examples:**
- `.txt`
- `.log`
- `.java`
- `.csv`
### 2) Binary Files
> **Binary files** store data in **raw binary format**, not as readable characters.

**Characteristics:**
- Not human-readable
- Meant to be processed by programs
- Data is stored as bytes

**Examples:**
- Images (`.jpg`, `.png`)
- Audio (`.mp3`)
- Video (`.mp4`)
- PDF and executable files
### File Path
1) **Absolute Path** -> `/home/user/documents/data.txt`
	- Gives full file location
	- Works from anywhere in the program
2) **Relative Path** -> `data.txt`
	- Shorter
    - Depends on where the program is running
### How Programs Access Files (Conceptual View)
A Java program does not work with a file directly like we open it manually.  
Instead, it follows a fixed and logical process to access any file.

Whenever a program works with a file, it generally does the following steps:
1. First, the program uses the **file path** to find where the file is located on the system.
2. Then, it opens a **stream**, which acts as a connection between the program and the file.
3. Using this stream, the program **reads data from the file or writes data into the file**.
4. Finally, after the work is done, the program **closes the file** to release system resources.

This same sequence is followed in almost all file-handling operations in Java.