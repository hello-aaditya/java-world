### Race-Condition
We have an SBI account and the following platforms are there which handles money transfer:
1. GPay
2. PhonePe
3. ATM

The account holder (name: Alpha) uses UPI platforms (GPay & PhonePe) whereas ATM (which belongs to the same account) is used by his friend (Beta).


Alpha decides to send an amount of INR 600/- to a shopkeeper.
At the same time, Beta is withdrawing an amount of INR 700/- from the same account.
consider, Alpha and Beta are not co-ordinating of money transfer information.

Alpha's Gpay initiates the money transfer. The Gpay-thread sees total balance = INR 1000/- . since sending amount is INR 600 and (600 < 1000), he can send the money.

The Gpay-thread takes 10 milliseconds to transfer. At the same time Beta checks through ATM and finds total amount = INR 1000/-. since the withdrawl amount is INR 700 and (700 < 1000), he can withdraw the money.
It means currently both are eligible to perform the money transfer process on his own.

Beta's ATM withdrawl also initiates within that same 10-millisecond window.

both succeed their payment process.
```text
Account Balance = 1000
GPay transfer   = 600
Remaining       = 1000 - 600 = 400
ATM withdrawal  = 700
Remaining       = 400 - 700 = -300
```

The bank is now in loss.
This is called a **Race condition**.

![race-condition](race-condition.drawio.svg)

> At a particular time (may be in nanosecond level), if multiple threads are trying to access or modify the shared object data then there is a chance that calculation of that object data may not be correct.
> This condition is called a **Race Condition**.

### How to prevent Race-Condition?
Race condition can be prevented by using synchronization.

**What is synchronization ?**
> One Thread at a time on a particular shared object.