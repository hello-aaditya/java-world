Consider that we are developing a payment gateway application.

The application supports multiple payment methods such as **UPI**, **Credit Card**, and **Wallet**.
All these payment methods perform one common operation—**payment**.

So, we decide to create a common `Payment` class.
```java
package com.payment;

public class Payment {

    public void pay(double amount) {
    
    }
    
}
```
At first glance, the `Payment` class appears as well designed because all payment class- **UPI**, **Credit Card**, and **Wallet** are expecting to perform a payment. Therefore, creating a common `pay(double amount)` method seems like a logical decision.

However, when we start implementing the `pay()` method, we encounter an important problem.

Suppose we write the logic for **UPI Payment**. The method validates the UPI ID, authenticates the UPI PIN, and then processes the payment.

Later, when we introduce **Credit Card Payment**, we realize that it does not require a UPI ID or UPI PIN. Instead, it needs card validation, CVV verification, and OTP authentication before processing the payment.

Similarly, **Wallet Payment** follows another process. It checks the wallet balance, deducts the required amount, and updates the remaining balance.

Now the question is:

**Which implementation should be written inside the `pay()` method of the `Payment` class?**
- Should it contain the logic for UPI Payment?
- Or Credit Card Payment?
- Or Wallet Payment?
![Problem-Without-Abstraction](abstraction.drawio.svg)

# Abstraction
> Abstraction is a process of writing program where developer exposes only required behavior of an object and hide core implementation.

in other word we can say-
> Abstraction focuses on projection means "what an object can do" rather than implementation means "how it performs that operation".

## Why Do We Need Abstraction?
Abstraction is required whenever a super class knows **which operations should exist**, but it cannot provide a common implementation because every sub class performs those operations differently.

## Benefits of Abstraction
1. Abstraction exposes only the required behavior of an object and hide its core implementation details.
2. Since the implementation details are hidden, means user interacts only with "***What*** an object does, not ***how*** it does it.
3. By keeping the implementation separate, abstraction improves code maintainability and it will become easier to debug also.
4. Abstraction helps in modularity by allowing to add new implementations with minimal or no changes in existing code.

## How Does Java achieve Abstraction?
Java provides two ways to achieve abstraction:
1. [**Abstraction Class**](10-ABSTRACT-CLASS.md)
2. Interface

