# Introduction
## Multitasking
Executing several tasks simultaneously is a concept of **Multitasking**.

There are two types of multitasking-
1. Process-Based Multitasking
2. Thread-Based Multitasking
### 1. Process-Based Multitasking
- Executing several tasks simultaneously where each task is a separate independent program (process), is called **Process-Based Multitasking**.

	**Example:**

	While typing a Java program in editor, we can listen audio songs from same system and at the same time we can download a file from internet.
- All these tasks will be executed simultaneously and independent of each other, hence it is **Process-Based Multitasking**.
- Process-Based Multitasking is best suitable at **OS-Level**.
### 2. Thread-Based Multitasking
- Executing several tasks simultaneously where each task is a separate independent part of the same program, is called **Thread-Based Multitasking** and each independent part is called a **Thread**.
- Thread-Based Multitasking is best suitable at **Programmatic-Level**.

### Advantages
> Whether it is Process-Based or Thread-Based, the main objective of multitasking is- **"to reduce response-time of the system and to improve performance"**.

### Applications
The main important application areas of Multithreading are:
1. To develop multimedia graphics.
2. To develop animations.
3. To develop video-games.
4. To develop web servers and application servers.

	etc.
	
>When compared with old languages, developing multithreaded applications in Java is very easy because Java provides inbuilt support for multithreading support with rich API (`Thread`, `Runnable`, `ThreadGroup` etc.)