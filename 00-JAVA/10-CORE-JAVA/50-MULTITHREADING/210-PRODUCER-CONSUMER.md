# Producer Consumer Problem
- Producer Thread is responsible to produce items to the queue and Consumer Thread is responsible to consume items from the queue.
- If queue is empty then Consumer thread will call `wait()` method and entered into WAITING state.
- After producing items to the queue, Prodcuer Thread is responsible to call `notify()` method then WAITING Consumer will get that notification and continue its execution with updated items
![producer-consumer-demo](producer-consumer-demo.drawio.svg)

### Example
**Task.java**
```java
public class Task {

	int data;
	boolean isDataAvailable = false;
	
	// produce
	public synchronized void produce(int data) throws InterruptedException {
		while (isDataAvailable) {
			System.out.println(
				"[" + Thread.currentThread().getName() + 
				"] is waiting..."
			);
			
			wait();
		}
		
		// produce the data
		this.data = data;
		System.out.println(
			" Produced the data: " + data
		);
		isDataAvailable = true;
		System.out.println(" Producer notifying the Consumer");
		notify(); // notify the Consumer so that Consumer can consume it. 
	}
	
	//consume
	public synchronized void consume() throws InterruptedException {
		while (!isDataAvailable) {
			System.out.println(
				"[" 
				+ Thread.currentThread().getName() 
				+ "] is waiting..."
			);
			
			wait();
		}
		
		System.out.println("Consuming the data : " + data);
		isDataAvailable = false;
		System.out.println(" Consumer notifying the Producer");
		notify(); // notify the producer so that producer can generate/produce more data
	}
	
}
```
`Task` acts as the shared resource between the Producer and Consumer threads. It contains a single `data` variable that works as the shared buffer and `isDataAvailable` to track whether data is available for consumption. The `produce()` method produces data and uses `wait()` when the buffer already contains data. The `consume()` method consumes data and uses `wait()` when the buffer is empty. `notify()` is used to wake the other waiting thread after producing or consuming data.

**Producer.java**
```java
public class Producer extends Thread {

	Task task;
	public Producer (Task task) {
		super();
		this.task = task;
	}
	
	@Override
	public void run() {
		for (int i=0; i<10; i++) {
			
			try {
				Thread.sleep(500);
				task.produce(i);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
			
		}
	}
}
```
generates values from `0` to `9` and passes each value to the `produce()` method of the shared `Task` object. The thread waits for 500 milliseconds between producing each item. Since Producer and Consumer use the same `Task` object, they operate on the same shared buffer.

**Consumer.java**
```java
public class Consumer extends Thread {

	Task task;
	
	public Consumer (Task task) {
		super();
		this.task = task;
	}
	
	@Override
	public void run() {
		for (int i=0; i<10; i++) {
			
			try {
				task.consume();
				Thread.sleep(500);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
			
		}
	}
}
```
`Consumer` represents the Consumer Thread and extends the `Thread` class. It repeatedly calls the `consume()` method of the shared `Task` object to consume the data produced by the Producer. The thread waits for 500 milliseconds after consuming each item. If the buffer is empty, the Consumer waits until the Producer produces new data and notifies it.

**Driver.java**
```java
public class Driver {

	public static void main(String[] args) {
		
		Task task = new Task();
		
		Producer producer = new Producer(task);
		Consumer consumer = new Consumer(task);
		
		producer.setName("Producer");
		consumer.setName("Consumer");
		
		consumer.start();
		producer.start();

	}

}
```
`Driver` contains the `main()` method and is responsible for creating the shared `Task` object and both threads. The same `Task` object is passed to both Producer and Consumer so that they share the same data and synchronization mechanism. The thread names are explicitly set to `"Producer"` and `"Consumer"`. Finally, both threads are started using `start()`.

>[!NOTE]
>In this code, we have used a **single buffer (`int data`)** to keep the Producer–Consumer concept simple and avoid increasing the complexity of the code. 
>In real applications, Producer–Consumer commonly uses a **shared queue/buffer containing multiple items**, and Java provides `BlockingQueue` for this purpose.