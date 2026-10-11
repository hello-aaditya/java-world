# ReentrantLock (c)
- It is introduced in Java 1.5
- It is the implementation class `Lock`(I) and it is direct child class of `Object`.
- Reentrant means a thread can acquired same lock multiple times without any issue.
- Internally ReentrantLock increment sThreads personal count whenever we call `lock()` method and decrement count value whenever Thread call `unlock()` method and Lock will be released whenever count reaches 0.
## Constructors

| #   | Constructor                                              | Explanation                                                                                                                                                                                                                                                                                                                                                               |
| --- | -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | `ReentrantLock l = new ReentrantLock();`                 | creates an instance of ReentrantLock.                                                                                                                                                                                                                                                                                                                                     |
| 2   | `ReentrantLock l = new ReentrantLock(boolean fairness);` | creates ReentrantLock with the given fairness policy.<br><br>- If the fairness is `true` then longest waiting Thread can acquire the lock if it is available. means it follows First-Come-First-Serve policy.<br><br>- If the fairness is `false` then which waiting thread will get the chance, we can't expect.<br><br>- The default value of `fairness` value `false`. |

---
Which of the following declarations are equals?
1. `ReentrantLock l = new ReentrantLock();`
2. `ReentrantLock l = new ReentrantLock(true);`
3. `ReentrantLock l = new ReentrantLock(false);`
4. All of the above

Answer → 1 and 3

---
## Important Methods of `ReentrantLock`

|   # | Method Name                            | Explanation                                                         |
| --: | -------------------------------------- | ------------------------------------------------------------------- |
|   1 | `void lock();`                         |                                                                     |
|   2 | `boolean tryLock();`                   |                                                                     |
|   3 | `boolean tryLock(long l, TimeUnit t);` |                                                                     |
|   4 | `void lockInterruptibly();`            |                                                                     |
|   5 | `void unlock();`                       |                                                                     |
|   6 | `int getHoldCount();`                  | Returns no. of holds on this lock by current Thread.                |
|   7 | `boolean isHeldByCurrentThread();`     | Returns `true` iff Lock is hold by current Thread.                  |
|   8 | `int getQueueLength();`                | Returns no. of Threads waiting for the Lock.                        |
|   9 | `Collection getQueuedThreads();`       | Returns a Collections of Threads which are waiting to get the Lock. |
|  10 | `boolean hasQueuedThreads();`          | Returns `true` if any Threads waiting to get the Lock.              |
|  11 | `boolean isLocked();`                  | Returns `true` if the Lock is acquired by any Thread.               |
|  12 | `boolean isFair();`                    | Returns `true` if the fairness policy is set with `true` value.     |
|  13 | `Thread getOwner();`                   | Returns the Thread which acquired the Lock.                         |
## Example-1
```java
import java.util.concurrent.locks.ReentrantLock;

public class ReentrantLockDemo {

	public static void main(String[] args) {
		
		ReentrantLock l = new ReentrantLock();
		
		l.lock();
		l.lock();
		
		System.out.println(l.isLocked()); // true
		System.out.println(l.isHeldByCurrentThread()); // true
		System.out.println(l.getQueueLength()); // 0
		
		l.unlock();
		
		System.out.println(l.getHoldCount()); // 1
		System.out.println(l.isLocked()); // true
		
		l.unlock();
		
		System.out.println(l.isLocked()); // false
		System.out.println(l.isFair()); // false

	}

}
```

## Example-2
**BankAccount.java**
```java
import java.util.concurrent.locks.ReentrantLock;

public class BankAccount {

	ReentrantLock l = new ReentrantLock();
	
	private int balance = 10000;

    public void send(int amount) {

    	l.lock(); // line-1
    	
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
        
        l.unlock(); // line-2
    }

    public int getBalance() {
        return balance;
    }
}
```
`BankAccount` represents a shared bank account accessed by multiple payment threads. A `ReentrantLock` is used to ensure that only one thread can execute the payment operation at a time. The `send()` method acquires the lock before reading and updating the balance, preventing both payment threads from modifying the balance simultaneously. After completing the payment, the lock is released using `unlock()`. The `balance` variable represents the current account balance.

**Driver.java**
```java
public class Driver {

	public static void main(String[] args) {
		
		BankAccount account = new BankAccount();
		
		Thread t1 = new Thread(() -> {
			account.send(2000);
		}, "GPay");
		
		Thread t2 = new Thread(() -> {
			account.send(3000);
		}, "PhonePe");
		
		t1.start();
		t2.start();
	}
}
```
`Driver` creates a single `BankAccount` object that is shared by both payment threads. `t1` represents a GPay payment of ₹2,000, while `t2` represents a PhonePe payment of ₹3,000. Both threads call the `send()` method on the same account object. The `ReentrantLock` inside `BankAccount` ensures that the two payment operations execute exclusively, one at a time.

- If we comment **line-1 (`l.lock()`)** and **line-2 (`l.unlock()`)**, both threads can enter `send()` concurrently. This can cause a **race condition**, and as a result we will get **incorrect/unpredictable final balance** and potentially irregular output.
- If we do **not** comment **line-1 (`l.lock()`)** and **line-2 (`l.unlock()`)**, the lock provides **mutual exclusion**, so only one thread can execute the locked section at a time. The other thread waits until the lock is released, and as a result we will get consistent final balance.