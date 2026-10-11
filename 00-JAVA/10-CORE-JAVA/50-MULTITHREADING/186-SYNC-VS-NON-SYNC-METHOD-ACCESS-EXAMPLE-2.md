![sync-and-non-sync-method-accessibility-example2](sync-and-non-sync-method-accessibility-example2.drawio.svg)
**BankAccount**
```java
public class BankAccount {

	private double balance = 10_000.0;
	
	// 1. SYNCHRONIZED STATIC METHODS
	// class-level lock
	public static synchronized void updatePaymentGateway() {
		System.out.println(
            "Updating payment gateway configuration..."
            + " [" + Thread.currentThread().getName() + "]"
        );

        try {
            Thread.sleep(3000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println(
            "Payment gateway configuration updated."
            + " [" + Thread.currentThread().getName() + "]"
        );
	}
	
	// SYNCHRONIZED STATIC METHODS
	// class-level lock
	public static synchronized void generateSettlementReport() {
		System.out.println(
            "Generating daily settlement report..."
            + " [" + Thread.currentThread().getName() + "]"
        );

        try {
            Thread.sleep(3000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println(
            "Settlement report generated."
            + " [" + Thread.currentThread().getName() + "]"
        );
	}
	
	
	// 2. NON-SYNCHRONIZED STATIC METHODS
	// class-level lock not require
	public static void generateTransactionId() {

        System.out.println(
            "Generating transaction ID..."
            + " [" + Thread.currentThread().getName() + "]"
        );
    }


    // class-level lock not require
    public static void validatePaymentAmount(double amount) {

        System.out.println(
            "Validating payment amount ₹" + amount
            + " [" + Thread.currentThread().getName() + "]"
        );
    }
    
    // 3. SYNCHRONIZED INSTANCE METHODS
    // object-level lock
    public synchronized void send(double amount) {

        System.out.println(
            "Sending ₹" + amount
            + " [" + Thread.currentThread().getName() + "]"
        );

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
    
    // object-level lock
    public synchronized void receive(double amount) {

        System.out.println(
            "Receiving ₹" + amount
            + " [" + Thread.currentThread().getName() + "]"
        );

        balance = balance + amount;

        System.out.println(
            "Receive completed. Balance = ₹" + balance
            + " [" + Thread.currentThread().getName() + "]"
        );
    }
    
    // 4. NON-SYNCHRONIZED INSTANCE METHODS
    // object-level lock not require
    public double getBalance() {

        System.out.println(
            "Reading account balance..."
            + " [" + Thread.currentThread().getName() + "]"
        );

        return balance;
    }
    
    // object-level lock not require
    public void displayAccountStatus() {

        System.out.println(
            "Displaying account status..."
            + " [" + Thread.currentThread().getName() + "]"
        );

        System.out.println(
            "Account is active."
        );
    }
    
}
```
>Contains all four types of methods used to demonstrate Java synchronization: 
>- synchronized static
>- non-synchronized static
>- synchronized instance
>- non-synchronized instance methods. 
>Static synchronized methods use the `BankAccount.class` lock, while synchronized instance methods use the object-lock of the particular `BankAccount` object.


**Driver**
```java
public class Driver {

	public static void main(String[] args) {
		
		BankAccount account = new BankAccount();
		
		Thread t1 = new Thread(() -> {
			BankAccount.updatePaymentGateway();
		}, "Gateway-Update");
		
		Thread t2 = new Thread(() -> {
			BankAccount.generateSettlementReport();
		}, "Settlement-Report");

		Thread t3 = new Thread(() -> {
			BankAccount.generateTransactionId();
		}, "Transaction-ID");
		
		Thread t4 = new Thread(() -> {
			BankAccount.validatePaymentAmount(2500);
		}, "Payment-Validation");
		
		Thread t5 = new Thread(() -> {
			account.send(2000);
		}, "GPay");
		
		Thread t6 = new Thread(() -> {
			account.receive(1500);
		}, "PhonePe");
		
		Thread t7 = new Thread(() -> {
			account.getBalance();
		}, "Balance-Check");
		
		Thread t8 = new Thread(() -> {
			account.displayAccountStatus();
		}, "Account-Status");
		
		t1.start();
		t2.start();
		t3.start();
		t4.start();
		t5.start();
		t6.start();
		t7.start();
		t8.start();
		
	}

}
```
> Creates the shared `BankAccount` object and eight threads. 
> The threads represent which methods share the **class lock**, which share the **object lock**, and which methods can execute **without acquiring either lock**.

**Output** (possible output)
```java
Reading account balance... [Balance-Check]
Updating payment gateway configuration... [Gateway-Update]
Displaying account status... [Account-Status]
Account is active.
Generating transaction ID... [Transaction-ID]
Validating payment amount ₹2500.0 [Payment-Validation]
Sending ₹2000.0 [GPay]
Payment gateway configuration updated. [Gateway-Update]
Send completed. Balance = ₹8000.0 [GPay]
Generating daily settlement report... [Settlement-Report]
Receiving ₹1500.0 [PhonePe]
Receive completed. Balance = ₹9500.0 [PhonePe]
Settlement report generated. [Settlement-Report]
```