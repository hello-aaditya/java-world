> I/O stands for **Input / Output**

# What is a Stream in Java?
> A **stream** is a path through which data flows between a program and a data source.

You can think of a stream as a **pipe or channel** that connects:
- the **program**
- and the **file (or any data source)**

### Important idea:

> Data never jumps directly between a file and a program —  
> it always flows through a **stream**.

## Why Does Java Use Streams?
Java uses streams because:
- Files, keyboard input, and network data all work in a similar way
- Streams provide a **uniform and controlled way** to handle data
- Streams allow Java to manage resources efficiently

**So whether the data comes from:**
- a file
- the keyboard
- or a network connection

Java treats all of them as **streams of data**.
## How Data Flows Between Program and File
When a Java program works with a file, data flows in one of two directions:
1) Reading Data (Input)
2) Writing Data (Output)
#### 1) Reading Data (Input)
- Data flows **from the file to the program**
- The program receives the data through an **input stream**
Example idea:
```markdown
File  --->  Program
```
#### 2) Writing Data (Output)
- Data flows **from the program to the file**
- The program sends the data through an **output stream**

Example idea:
```markdown
Program  --->  File
```

> The direction of data flow decides whether an **input stream** or an **output stream** is used.
>
>- Reading → Input stream
>- Writing → Output stream

