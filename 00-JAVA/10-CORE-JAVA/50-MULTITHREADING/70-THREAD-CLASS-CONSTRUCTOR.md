|     # | Constructor                                                                      | Explanation                                                          |
| ----: | -------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| **1** | `Thread t = new Thread();`                                                       | Default constructor                                                  |
| **2** | `Thread t = new Thread(Runnable r);`                                             | Creates Thread using `Runnable`                                      |
| **3** | `Thread t = new Thread(String name);`                                            | Creates Thread with a name                                           |
| **4** | `Thread t = new Thread(Runnable r, String name);`                                | Creates Thread using `Runnable` and a name                           |
| **5** | `Thread t = new Thread(ThreadGroup g, String name);`                             | Creates Thread using `ThreadGroup` and a name                        |
| **6** | `Thread t = new Thread(ThreadGroup g, Runnable r);`                              | Creates Thread using `ThreadGroup` and `Runnable`                    |
| **7** | `Thread t = new Thread(ThreadGroup g, Runnable r, String name);`                 | Creates Thread using `ThreadGroup`, `Runnable`, and name             |
| **8** | `Thread t = new Thread(ThreadGroup g, Runnable r, String name, long stackSize);` | Creates Thread using `ThreadGroup`, `Runnable`, name, and stack size |
## Different Approach to define a Thread (not recommend to use)
**Define a Thread**
```java
class MyThread extends Thread {
	
	@Override
	public void run() {
		System.out.println("Thread 0");
	}
}
```
**Start a Thread**
```java
public class ThreadDemo {
	public static void main(String[] args) {
		
		MyThread t = new MyThread();
		Thread t1 = new Thread(t);
		
		t1.start();
		System.out.println("main Thread");
	}
}
```
**Possible Ouputs:**
Output-1
```text
Thread 0
main Thread
```
Output-2
```text
main Thread
Thread 0
```
