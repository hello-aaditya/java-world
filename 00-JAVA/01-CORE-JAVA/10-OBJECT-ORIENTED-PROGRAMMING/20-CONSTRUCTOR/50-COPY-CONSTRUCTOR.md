# Copy Constructor
> A Copy Constructor** is a constructor which is used to create a new object using an existing object of the same class.
> Java does not provide a built-in copy constructor automatically like C++.

## Syntax
```java
class Classname {
	ClassName(ClassName obj) {
		// BODY
	}
}
```
#### Example
```java
public class Invoice {

    private String invoiceNumber;
    private String customerName;
    private double amount;
    private String paymentStatus;

    public Invoice(String invoiceNumber,
                   String customerName,
                   double amount,
                   String paymentStatus) {

        this.invoiceNumber = invoiceNumber;
        this.customerName = customerName;
        this.amount = amount;
        this.paymentStatus = paymentStatus;
    }

    // Copy Constructor
    public Invoice(Invoice invoice) {
        this.invoiceNumber = invoice.invoiceNumber;
        this.customerName = invoice.customerName;
        this.amount = invoice.amount;
        this.paymentStatus = invoice.paymentStatus;
    }
}
```

```java
Invoice oldInvoice = new Invoice("INV-1001", "Infosys", 125000, "PENDING");

Invoice newInvoice = new Invoice(oldInvoice);
```