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
5. If an exception occurs inside the `try` block, the JVM **immediately stops executing the remaining statements** in that `try` block and transfers control to a matching `catch` block.
6. If no exception occurs, all statements inside the `try` block execute normally, and the associated `catch` blocks are skipped.
7. Variables declared inside `try` are local to that block — not visible inside `catch` or `finally`.
	If a value computed inside `try` is needed later (in `catch` or `finally`, or after the block), declare that variable _before_ the `try` and only assign it inside.
8. A `try` block can contain another complete `try`-`catch` inside it.
9. If the inner `try` block does not have a matching `catch` block for the thrown exception, the exception propagates to the outer `try` block, where the JVM searches its `catch` blocks for a matching handler.
## Rules of `finally` block
- A `catch` block **must always be associated with a `try` block**. It cannot exist independently.
- A `catch` block **must declare exactly one exception parameter**.
    ```java
    catch (ArithmeticException e)
    ```
- A single `try` block **can have multiple `catch` blocks** to handle different exception types.
- When multiple `catch` blocks are used, **more specific exceptions must be placed before more general exceptions**. Otherwise, the code will result in a compile-time error.
- The JVM executes **only the first matching `catch` block**. The remaining `catch` blocks are skipped.
- If no `catch` block matches the thrown exception, the exception **propagates to the caller**. If it remains unhandled, the JVM prints the exception details and stack trace, then terminates the program.
- A `catch` block **cannot appear without a preceding `try` block**.
- - `catch` must immediately follow `try` or another `catch` — nothing else can sit between them.
- `try` can have zero `catch` blocks only if a `finally` block is present.