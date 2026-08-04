# How do we handle Exception?
An exception is handled by enclosing the risky code inside a `try` block and writing one or more `catch` blocks to handle specific exceptions. This prevents the program from terminating abruptly and allows normal execution to continue.
## `try-catch` block
> A `try` block is a block of code that contains statements which may throw an exception during program execution. If an exception occurs inside the `try` block, the JVM immediately stops executing the remaining statements in the `try` block and transfers control to a matching `catch` block.

## Syntax of `try-catch` block
```java
try {
	// CODE THAT MAY THROW AN EXCEPTION
} catch (ExceptionType e) {
	// CODE TO HANDLE THE EXCEPTION
}
```
## Solution of Previous Problem
```java
package com.billing;

public class PricingService {

    public static void main(String[] args) {

        int totalAmount = 5000;
        int quantity = 0;
        processOrder(totalAmount, quantity);
    }

    static void processOrder(int totalAmount, int quantity) {
        int unitPrice = calculateUnitPrice(totalAmount, quantity);
        System.out.println("Unit Price = " + unitPrice);
    }

    static int calculateUnitPrice(int totalAmount, int quantity) {
        try {
            return divide(totalAmount, quantity);
        } catch (ArithmeticException e) {
            System.out.println("Exception Handled in calculateUnitPrice()");
            return 0;
        }
    }

    static int divide(int dividend, int divisor) {
        return dividend / divisor;      // Exception occurs here
    }
}
```
>[!Note]
>The `catch` sits in `calculationPrice()` because that's the lowest layer that knows how to recover meaningfully- falling back to a zero unit price.
>`processOrder()` and `main()` have no business context to decide that. so the exception shouldn't be allowed to propagate that for up.
## Rules of `try`Block
1. A `try` block **must be followed by at least one `catch` block or a `finally` block**. A `try` block cannot exist alone.
2. A `try` block **cannot appear without braces (`{}`)**, even if it contains only a single statement.
3. A single `try` block **can be followed by multiple `catch` blocks**, each handling a different type of exception.
4. A `try` block **can have only one `finally` block**.
5. If an exception occurs inside the `try` block, the JVM **immediately stops executing the remaining statements** in that `try` block and searches for a matching `catch` block.
6. If no exception occurs, all statements inside the `try` block execute normally, and the associated `catch` blocks are skipped.