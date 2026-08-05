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
```java
package com.practice;

import java.math.BigDecimal;
import java.math.RoundingMode;

public class HeapDiagnostics {

	public static void main(String[] args) {
		Runtime runtime = Runtime.getRuntime();

		long maxBytes       = runtime.maxMemory();         // -Xmx ceiling
		long committedBytes = runtime.totalMemory();       // heap committed so far
		long freeBytes      = runtime.freeMemory();        // free space within committed
		long usedBytes      = committedBytes - freeBytes;  // actually in use
		long availableBytes = maxBytes - usedBytes;        // real headroom to -Xmx

		System.out.println("Max Heap (-Xmx):       " + toGb(maxBytes) + " GB");
		System.out.println("Committed Heap:        " + toGb(committedBytes) + " GB");
		System.out.println("Used Heap:             " + toGb(usedBytes) + " GB");
		System.out.println("Free (within committed): " + toGb(freeBytes) + " GB");
		System.out.println("Available (to -Xmx):   " + toGb(availableBytes) + " GB");
	}

	public static BigDecimal toGb(long bytes) {
		BigDecimal value = BigDecimal.valueOf(bytes)
				.divide(BigDecimal.valueOf(1024L * 1024 * 1024), 10, RoundingMode.HALF_UP);
		return value.setScale(3, RoundingMode.HALF_UP);
	}
}
```
## `-Xmx4G` vs `-Xms4G`
| VM Argument | Meaning           | Controls                                                                                                | Example  |
| ----------- | ----------------- | ------------------------------------------------------------------------------------------------------- | -------- |
| `-Xms`      | Initial Heap Size | The `-Xms` option specifies the **initial heap size** allocated to the JVM when the application starts. | `-Xms5G` |
| `-Xmx`      | Maximum Heap Size | The `-Xmx` option specifies the **maximum heap size** the JVM is allowed to use.                        | `-Xmx5G` |
### `-Xms5G` (Initial Heap Size)
```text
-
│
├── X   → Non-standard JVM option
├── ms  → Initial Memory Size
└── 4G  → 4 Gigabytes
```
means:

> "Start the JVM with a heap of **5 GB**."

The JVM begins with a heap of approximately 5 GB

#### Heap Growth
```text
JVM Starts

Heap
┌────────────────────────────┐
│                            │ 5 GB
│                            │
│                            │
└────────────────────────────┘
```
The application starts with a large heap immediately available.
#### `-Xmx5G` (Maximum Heap Size)
```text
-
│
├── X   → Non-standard JVM option
├── mx  → Maximum Memory Size
└── 4G  → 4 Gigabytes
```
means:

> "The heap may grow up to **5 GB**, but it doesn't have to start there."

Initially, the heap might be much smaller.
```text
JVM Starts

Heap
┌───┐
│   │ 256 MB (example)
└───┘
```
As more objects are created:
```text
256 MB

↓

512 MB

↓

1 GB

↓

3 GB

↓

5 GB (Maximum)
```
The heap grows only when necessary.
### Both Together
Most applications specify both values.
Example:
```java
-Xms512M -Xmx5G
```
This means:
- Start with **512 MB**.
- Grow gradually up to **5 GB**.
```text
Startup

512 MB

↓

Application creates objects

↓

1 GB

↓

2 GB

↓

5 GB (Maximum)
```
### What if both are the same?
Example:
This means:
- Initial heap = 5 GB
- Maximum heap = 5 GB
So the heap size never needs to expand during execution.
```text
Startup

5 GB

↓

Application runs

↓

Still 5 GB
```
This avoids heap expansion, which can reduce resizing overhead in long-running applications. It's common for applications whose memory requirements are well understood.
