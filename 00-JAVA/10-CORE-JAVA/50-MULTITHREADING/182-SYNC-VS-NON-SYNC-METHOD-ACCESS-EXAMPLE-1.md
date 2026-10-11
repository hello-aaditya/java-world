Example of- 
When a Thread executes any `synchronized` method, the other Threads are not allowed to execute any `synchronized` method on that object simultaneously.

But other Threads are allowed to execute any non-synchronized method simultaneously. [Lock concept is implements based on object but not based on method].
![sync-and-non-sync-method-accessibility](sync-and-non-sync-method-accessibility.drawio.svg)

---
**BankAccount**
```java
public class BankAccount {

	private double balance = 10_000.0;
	
	// Synchronized method
	public synchronized void send (double amount) {
		
		System.out.println(
			"Sending ₹" + amount
			+ " [" + Thread.currentThread().getName() + "]"
		);
		
		// consider sending an amount takes 3 seconds
		
		try {
			Thread.sleep(3000);
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		
		balance = balance - amount;
		
		System.out.println(
            "Send completed. Balance = ₹" + balance
            + " [" + Thread.currentThread().getName() + "]"
        );
	}
	
	// Synchronized method
	public synchronized void receive (double amount) {
			
		System.out.println(
			"Receiving ₹" + amount
			+ " [" + Thread.currentThread().getName() + "]"
		);
		
		// consider receiving an amount takes 3 seconds
		
		try {
			Thread.sleep(3000);
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		
		balance = balance + amount;
		
		System.out.println(
            "Receiving completed. Balance = ₹" + balance
            + " [" + Thread.currentThread().getName() + "]"
        );
	}
	
	// non-synchronized method
	public double getBalance() {

		// consider fetching balance takes 2 seconds
		try {
			Thread.sleep(2000);
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		
        System.out.println(
            "Reading account balance..."
            + " [" + Thread.currentThread().getName() + "]"
        );

        return balance;
    }
}
```
> Contains the shared bank account state and its operations. 
> `send()` and `receive()` are synchronized methods, while `getBalance()` is a non-synchronized method to show synchronized vs non-synchronized method access on the same object.

**GPayThread**
```java
public class GpayThread extends Thread {

	private BankAccount account;
	
	GpayThread (String name, BankAccount account) {
		super(name);
		this.account = account;
	}
	
	@Override
	public void run() {
		account.send(2000);
	}
}
```
> Represents a GPay transaction thread. It calls the `send()` synchronized method on the shared `BankAccount` object.

**PhonePeThread**
```java
public class PhonePeThread extends Thread {

	private BankAccount account;
	
	PhonePeThread (String name, BankAccount account) {
		super(name);
		this.account = account;
	}
	
	@Override
    public void run() {
        account.receive(1500);
    }
}
```
> Represents a PhonePe transaction thread. It calls the `receive()` synchronized method on the same shared `BankAccount` object, so it must wait if another thread already holds the object's lock.

**BalanceThread**
```java
public class BalanceThread extends Thread {

	private BankAccount account;

    BalanceThread(String name, BankAccount account) {
        super(name);
        this.account = account;
    }

    @Override
    public void run() {

        double balance = account.getBalance();

        System.out.println(
            "Current balance = ₹" + balance
            + " [" + Thread.currentThread().getName() + "]"
        );
    }
}
```
> Represents a balance-checking thread. It calls the non-synchronized `getBalance()` method, so it can execute even when another thread is executing a synchronized method on the same `BankAccount` object.

**Driver**
```java
public class Driver1 {

	public static void main(String[] args) {
		
		BankAccount account = new BankAccount();
		
		GpayThread t1 = new GpayThread("GPay", account);
		
		PhonePeThread t2 = new PhonePeThread("PhonePe", account);
		
		BalanceThread t3 = new BalanceThread("Balance-Check", account);
		
		t1.start();
		t2.start();
		t3.start();

	}

}
```
> Creates one shared `BankAccount` object and three threads, then starts them to demonstrate that synchronized methods block other synchronized methods on the same object, while a non-synchronized method can execute simultaneously.