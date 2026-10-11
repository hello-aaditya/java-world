# What is a Process?
> - A program under execution is called a **Process**.
> - A Process has its own memory space and system resources.
> - **A Process's memory is logically isolated from other processes**. One process normally cannot directly access another process's memory.
>   Example: **JVM**
# What is a Thread ?
> - Within a process, a smallest unit of execution is called a **Thread**.
> - Within a process, Threads share process's memory space and system resources.
> - In Java, every program has at least one Thread: the **`main` thread**.
## Example of Process and Threads
![process-and-threads-example](process-and-threads-example.drawio.svg)

**Consider a customer paying money to a merchant through the PhonePe app:**
  - The running PhonePe app can be considered a **Process**.
  - Within that process, different threads can perform different work, such as:
	- Adding a payee (via: **UPI ID, Mobile Number, or Bank A/C Details**)
	- Processing the money transfer
	- Get transaction notification
## Identifying the Currently Executing Thread
```java
public class IdentifyYourThread {

	public static void main(String[] args) {
		
		String threadName = Thread.currentThread().getName(); 
		
		System.out.println(
			"This code is executing by [" + threadName + "] Thread"
		);// output ➔ This code is executing by [main] Thread
		
		System.out.println(
			"This is my Hello-World Program"
		);
	}
}
```
#### `main` Thread
> When a Java application starts, the **JVM creates and starts the main thread**, which executes the `main()` method.
## Defining a Thread
>We can define a Thread in the following two ways:
>1. [By extending `Thread` class](40-DEFINE-THREAD-BY-EXTENDING-THREAD-CLASS.md)
>2. [By implementing `Runnable` interface](50-DEFINE-THREAD-BY-IMPLEMENTING-RUNNABLE-INTERFACE.md)

![define-a-thread](define-a-thread.drawio.svg)