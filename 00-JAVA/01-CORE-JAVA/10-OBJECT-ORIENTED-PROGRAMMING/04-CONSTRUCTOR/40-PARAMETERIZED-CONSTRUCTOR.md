# Parameterized Constructor
> A **Parameterized Constructor** is a type of constructor which is explicitly written by developer and which accepts some parameters. 
> It allows developer to pass arguments at the time of object creation. 

## Syntax
```java
class Classname {
	
	// DECLARE INSTANCE VARIABLES
	int number;
	String text;
	
	// PARAMETERIZED CONSTRUCTOR
	ClassName(int number, String text) {
		this.number = number;
		this.text = text;
	}
}
```
#### Example
```java
package com.publicBank;

public class Account {

    private String accountId;
    private double balance;
    private float interestRate;
    private boolean isActive;

    // PARAMETERIZED CONSTRUCTOR
    public Account(String accountId,
                   double balance,
                   float interestRate,
                   boolean isActive) {

        this.accountId = accountId;
        this.balance = balance;
        this.interestRate = interestRate;
        this.isActive = isActive;
    }

    void showProfile() {
        System.out.println(
            "Account ID        : " + accountId +
            "\nBalance           : " + balance +
            "\nInterest Rate     : " + interestRate +
            "\nIs Account Active : " + isActive
        );
    }

    public static void main(String[] args) {

        Account account = new Account(
                "ACC1001",
                50000.00,
                3.5f,
                true
        );

        account.showProfile();
    }

}
```
#### Output
```text
Account ID        : ACC1001
Balance           : 50000.0
Interest Rate     : 3.5
Is Account Active : true
```

