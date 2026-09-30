# Constructor Validation — Fail-Fast Principle

## Problem
#### Example
```java
public class Account {

    private String accountId;
    private double balance;

    public Account(String accountId, double balance) {
        this.accountId = accountId;
        this.balance = balance;
    }

    void showProfile() {
        System.out.println(
                "Account ID : " + accountId +
                "\nBalance    : " + balance
        );
    }

    public static void main(String[] args) {

        Account account = new Account(null, -5000);

        account.showProfile();
    }

}
```
#### Output
```java
Account ID : null
Balance    : -5000.0
```
> Does this object represent a valid bank account?

Obviously, **No.**
An account cannot have
- a `null` Account ID
- a negative balance
But here Java successfully created the object in an Invalid State.

## Invalid State
> An object is said to be in an invalid state when its field values fail to represent a valid real-world entity according to the business rules and constraints of that class.

In the above example,
```java
Account ID : null
Balance    : -5000.0
```
fails the business rules of an `Account`.

The best solution is to prevent such an object from being created in the first place.

## Fail-Fast Principle
> The Fail-Fast Principle states that a constructor should validate all incoming arguments as early as possible before initializing the object's fields and immediately reject invalid data by throwing an appropriate exception, so that an object is never created in an invalid state.

