# Exception
> An _exception_ is an event, which occurs during the execution of a program and disrupts the normal flow of the program's instructions.

- When an error occurs within a method, the method creates an object and hands it off to the runtime system. This object is known as an **exception object**. 
- The exception Object contains three information:
	1. Exception Type
	2. Error Message
	3. Stack Trace (method names, file names, line numbers)
- The process of creating an exception object and handing it to the runtime system is called **throwing an exception**.
- After a method throws an exception, the runtime system attempts to find a matching exception handler. The ordered list of methods that were called to reach the method where the exception occurred is known as the **Call Stack**.
- The runtime system searches the Call Stack in reverse order, starting from the method where the exception occurred and moving back through each calling method. If it finds a matching exception handler (`catch` block), the exception is passed to that handler.
- If the runtime system searches the entire Call Stack without finding a matching exception handler, the exception remains uncaught. In this case, the JVM prints the **Stack Trace** and terminates the program.

![](./images/exception-process.drawio.svg)
#### Example
```java
package com.billing;

public class PricingService {

    public static void main(String[] args) {
        int totalAmount = 5000;
        int quantity = 0;
        calculateUnitPrice(totalAmount, quantity);
    }

    static void calculateUnitPrice(int totalAmount, int quantity) {
        int unitPrice = computeUnitPrice(totalAmount, quantity);
        System.out.println("Unit Price = " + unitPrice);
    }

    static int computeUnitPrice(int totalAmount, int quantity) {
        return totalAmount / quantity; // ArithmeticException here
    }
}
```

![Exception Call Stack](./images/exception-call-stack.drawio.svg)

>[!NOTE] 
`quantity` is zero, so `divide()` triggers `ArithmeticException`. the call stack is four frames deep: 
`divide() ← MAIN() → PROCESSORDER() → CALCULATEUNITPRICE() → DIVIDE()`.

#### Solution Code
```java
package com.mathematics;

public class Driver {

    public static void main(String[] args) {

        int operand1 = 10;
        int operand2 = 0;
        processCalculation(operand1, operand2);
    }

    static void processCalculation(int operand1, int operand2) {
        int result = calculate(operand1, operand2);
        System.out.println("Result = " + result);
    }

    static int calculate(int operand1, int operand2) {
    	try {
    		return divide(operand1, operand2);
    	} catch (ArithmeticException e) {
    		System.out.println("Exception Handled in calculate()");
    		return 0;
    	}
    }

    static int divide(int dividend, int divisor) {
        return dividend / divisor;      // Exception occurs here
    }
}
```