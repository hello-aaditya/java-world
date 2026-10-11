# Different Objects (Not Shared), Different Locks
**BankAccount**
```java
public class BankAccount {

	private int balance = 10000;

	    public synchronized void send(int amount) {

	        System.out.println(
	            "Payment started by "
	            + Thread.currentThread().getName()
	        );

	        int currentBalance = balance;

	        try {
	            Thread.sleep(2000);
	        } catch (InterruptedException e) {
	            e.printStackTrace();
	        }

	        balance = currentBalance - amount;

	        System.out.println(
	            "Payment completed by "
	            + Thread.currentThread().getName()
	            + " | Balance = ₹" + balance
	        );
	    }

    public int getBalance() {
        return balance;
    }
}
```
**Driver.java**
```java
public class Driver {

	public static void main(String[] args) {
		
		BankAccount account1 = new BankAccount();
		BankAccount account2 = new BankAccount();
		
		
		Thread t1 = new Thread(() -> {
			account1.send(2000);
		}, "GPay");
		
		Thread t2 = new Thread(() -> {
			account2.send(3000);
		}, "PhonePe");
		
		t1.start();
		t2.start();
	}

}
```
Here, `account1` and `account2` are **two different `BankAccount` objects**, so they have **two different object locks**.
```text
t1 → account1 → synchronized send() → 🔒 obj1 lock

t2 → account2 → synchronized send() → 🔒 obj2 lock
```
Even though `send()` which is **instance method**, is `synchronized`, we will get irregular output because threads are operating on different Java objects.

Therefore, both threads can execute the `synchronized` method **simultaneously**.

> If multiple threads are operating on same Java objects then `synchronization` is required.
> If multiple threads are operating on multiple Java objects then `synchronization` is not required.
