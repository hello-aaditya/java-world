### Product Management System

This practice set will demonstrate the use of the `this` keyword in Java through a scenario involving a product management system.

### Subtask 1: Define a Class with a Parameterized Constructor Using this Keyword

**Problem Statement:**

Create a class named `Product` with a parameterized constructor to initialize the product's details such as name, price, and category. Use the `this` keyword to differentiate between instance variables and parameters.

**Detailed Instructions:**

1. Create the Product class:
   - Declare three instance variables: `productName` (String), `productPrice` (double), and `productCategory` (String).
   - These variables will store the product's name, price, and category.

2. Define a parameterized constructor:
   - Create a constructor with three parameters: `String productName`, `double productPrice`, and `String productCategory`.
   - Inside the constructor, use the `this` keyword to assign the parameter values to the instance variables (`this.productName`, `this.productPrice`, `this.productCategory`).

3. Create a method `displayDetails()`:
   - This method should print out the details of the product in a formatted manner.
   - Expected output format:
     ```
     Product Name: Laptop
     Product Price: $1200.5
     Product Category: Electronics
     ```

### Subtask 2: Create Objects Using the Parameterized Constructor and Display Details

**Problem Statement:**

Create multiple Product objects using the parameterized constructor and display their details.

**Detailed Instructions:**

1. In the `main()` method of the Main class:
   - Create three Product objects using the parameterized constructor.
   - Use the following values for each product:
     - Product 1: Name = "Laptop", Price = 1200.50, Category = "Electronics"
     - Product 2: Name = "Chair", Price = 150.75, Category = "Furniture"
     - Product 3: Name = "Book", Price = 25.99, Category = "Education"

2. Call the `displayDetails()` method for each object:
   - This will display the details of each product, allowing you to verify that the objects were initialized correctly.

## Complete Code

```java
class Product {
    String productName;
    double productPrice;
    String productCategory;
    
    public Product(String productName, double productPrice, String productCategory) {
        this.productName = productName;
        this.productPrice = productPrice;
        this.productCategory = productCategory;
    }
    
    public void displayDetails() {
        System.out.println("Product Name: " + productName);
        System.out.println("Product Price: $" + productPrice);
        System.out.println("Product Category: " + productCategory);
    }
}

public class Main {
    public static void main(String[] args) {
        Product product1 = new Product("Laptop", 1200.50, "Electronics");
        Product product2 = new Product("Chair", 150.75, "Furniture");
        Product product3 = new Product("Book", 25.99, "Education");
        
        product1.displayDetails();
        product2.displayDetails();
        product3.displayDetails();
    }
}
````

## Expected Output

```output
Product Name: Laptop
Product Price: $1200.5
Product Category: Electronics
Product Name: Chair
Product Price: $150.75
Product Category: Furniture
Product Name: Book
Product Price: $25.99
Product Category: Education
```        