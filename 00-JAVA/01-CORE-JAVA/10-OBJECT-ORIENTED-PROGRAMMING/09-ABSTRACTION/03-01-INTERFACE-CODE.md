# **Practice Question: Bank Operations Using Interface (Markdown Version)**

### Q1. Implement a simple banking system using an interface and a concrete class.

Create an interface named **`BankOperations`** containing the following abstract methods:

1. `openAccount(String name, long accountId, double initialAmount)`
2. `deposit(double amount)`
3. `withdraw(double amount)`
4. `checkBalance()`
5. `closeAccount()`
---
### **Requirements**

#### 1. Create an interface
- File: `BankOperations.java`
- It must contain **all five abstract methods** listed above.

---

#### 2. Create a concrete class
- Class name: **`SavingAccount`**
- It should **implement `BankOperations`**.
- Add private fields:
    - `String name`
    - `long accountId`
    - `double balance`
        
- Implement all methods:
    - `openAccount()` sets initial values.
    - `deposit()` increases balance.
    - `withdraw()` decreases balance (only if enough balance exists).
    - `checkBalance()` prints current balance.
    - `closeAccount()` resets all fields and prints confirmation.
---
#### 3. Create a Main Class
- Class name: **`BankMain`**
- Use `Scanner` to take user inputs:
    - account holder name
    - account ID
    - initial amount
    - menu choices (Deposit, Withdraw, Check Balance, Close Account, Exit)
- Create an interface reference:
    ```java
    BankOperations bo = new SavingAccount();
    ```
- Call methods based on user choice.
---
### Expected Console Menu
```
1. Deposit
2. Withdraw
3. Check Balance
4. Close Account
5. Exit
```
---
### Solution
#### BankOperations.java (Interface)
```java
package interfaces;

public interface BankOperations {
	
	void openAccount(String name, long accountId, double initialAmount);
	void deposit(double amount);
	void withdraw(double amount);
	void checkBalance();
	void closeAccount();
}
```
#### BankMain.java
```java
package interfaces;

import java.util.Scanner;

public class BankMain {

	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		System.out.print("Enter Account Holder Name: ");
		String name = input.nextLine();
		
		System.out.print("Enter Account ID: ");
		long accID = input.nextLong();
		
		System.out.print("Enter Initial Amount: ");
		double amount = input.nextDouble();
		
		
		BankOperations bo = new SavingAccount();
		bo.openAccount(name, accID, amount);
		
		int choice;
		
		do {
			System.out.println("\n1. Deposit\n2. Withdraw\n3. Check Balance\n4. Close Account\n5. Exit");
			System.out.print("Enter Choice: ");
			choice = input.nextInt();
			
			switch(choice) {
				case 1: 
					System.out.print("Enter amount: ");
					bo.deposit(input.nextDouble());
					break;
				
				case 2:
					System.out.print("Enter amount: ");
					bo.withdraw(input.nextDouble());
					break;
					
				case 3:
					bo.checkBalance();
					break;
					
				case 4:
					bo.closeAccount();
					choice = 5;
					break;
					
				case 5:
					System.out.println("Thank You!");
					break;
					
				default:
					System.out.println("Invalid choice");
			}
		} while(choice != 5);

		input.close();
	}
}
```
