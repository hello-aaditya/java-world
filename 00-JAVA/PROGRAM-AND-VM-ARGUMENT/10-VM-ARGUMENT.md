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
