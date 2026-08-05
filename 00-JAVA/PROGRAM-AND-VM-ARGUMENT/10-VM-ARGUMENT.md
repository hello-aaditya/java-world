# VM Argument
> **VM (Virtual Machine) Arguments** are command-line options passed to the **Java Virtual Machine (JVM)** before the Java application starts. They are used to configure the JVM's behavior, such as memory allocation, garbage collection, system properties, assertions, and debugging options. VM arguments affect **how the JVM executes the application**, not the application's business logic.

## Applications of VM Arguments
VM Arguments are commonly used for:
- Configuring heap memory (`-Xms`, `-Xmx`)
- Selecting or tuning the Garbage Collector
- Passing system properties (`-Dkey=value`)
- Enabling assertions (`-ea`)
- Generating heap dumps on OutOfMemoryError
- Enabling remote debugging
- Logging JVM information
- Configuring JVM performance for different environments (development, testing, production)
## Increasing Heap Size using VM Arguments
The heap is the runtime memory area where Java objects are allocated.

By default, the JVM automatically determines the initial and maximum heap size based on the system configuration.

If an application requires more memory, the heap size can be increased using VM arguments.

### Initial Heap Size
```java
-Xms512M
```
Starts the JVM with an initial heap of **512 MB**.
### Maximum Heap Size
```java
-Xmx4G
```
Allows the heap to grow up to a **maximum of 4 GB**.

**Important**
`-Xmx4G` **does not immediately allocate 4 GB of RAM.**

It only tells the JVM:
> "You are allowed to increase the heap up to 4 GB if the application requires it."

The heap grows gradually as more objects are created.
## How to Verify that the Heap Size Has Increased
